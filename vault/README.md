# Gestion des secrets avec Vault

## Création d'un secret via Vault WebUI

Sur la page **Services externes** se trouve la tuile de Vault, cliquer dessus.

Une nouvelle fenêtre s'ouvre pour s'authentifier, cliquer sur le bouton bleu **Sign in with OIDC provider**:
![login](./img/login.png)

---

Une fois authentifié, vous retrouvez un espace associé à votre projet (dans la nomenclature Hashicorp ce nom sera référencé en tant que **mount**).
![coffres](./img/secret-engine.png)

---

Pour créer un nouveau secret, cliquer sur le bouton à droite **Create secret +**, et remplir les champs suivants:

- **Path for this secret**: le chemin vers le secret dans le coffre. L'arborescence, même complexe, est automatiquement créée (dans la nomenclature Hashicorp ce nom sera référencé en tant que **path**).
- **Secret data**: les données secrètes sous la forme clé-valeur
![create_secret](/img/guide/secrets/vso/create_secret.png)

Cliquer sur le bouton bleu **Save** pour enregistrer le nouveau secret.

---

Une fois le secret créé, vault renvoie vers l'arborescence du secret (dans l'exemple *formation/*, où se trouve bien le secret **exemple**):
![new secret list](./img/secret_created.png)

## Récupération du secret depuis un deploiement

L'opérateur [Vault Secret Operator](https://developer.hashicorp.com/vault/tutorials/kubernetes/vault-secrets-operator) est disponible afin de récupérer les secrets auprès de vault.

Pour chaque projet créé dans la console, des objets de type `VaultConnection` et `VaultAuth` sont automatiquement créés afin de pouvoir authentifier le projet.

La récupération d'un secret passe par la création d'un objet de type `VaultStaticSecret` qui lui-même va générer un secret kubernetes.

Créer le fichier suivant :

```yaml
apiVersion: secrets.hashicorp.com/v1beta1
kind: VaultStaticSecret
metadata:
  name: my-vault-secret
spec:
  vaultAuthRef: vault-auth # Nom du VaultAuth, toujours vault-auth dans le cas de CPiN
  mount: tutoplec # Nom du coffre dans vault (correspond slug du projet visible depuis la console, en général le nom du projet)
  path: formation/exemple # Chemin vers le secret
  type: kv-v2 # Type du coffre, toujours kv-v2 dans le cas de CPiN
  destination:
    name: mysecret-vault # Nom du secret kubernetes que l'opérateur va créer
    create: true
```

Ce fichier ne contient pas d'information sensible et peut donc être ajouter au repo d'infrastructure.

Ajouter ce fichier au chart HELM de deploiement et vérifiez qu'un secret est bien créé depuis ArgoCD :

![secret argoCD](./img/argo-vault-secret.png)

et le detail :

![secret argoCD](./img/argo-vault-secret-detailed.png)

Il est maintenant possible de modifier le deploiement pour référencer ce secret et changer :

```yaml
            - name: SPRING_DATASOURCE_PASSWORD
              valueFrom:
                secretKeyRef:
                  key: password
                  name: mysecret-vault
```
