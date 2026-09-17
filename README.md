# Gestion des secrets sur CPiN

Vous en êtes à l'étape 5 de la formation CPiN :

1. [Gestion des projets CPiN](https://github.com/cloud-pi-native/formation-cpin-gestion-projet)
2. [Application d'exemple pour déploiement sur CPiN](https://github.com/cloud-pi-native/formation-cpin-repo-applicatif)
3. [Gestion des artefacts sur CPiN](https://github.com/cloud-pi-native/formation-cpin-harbor-trivy)
4. [Chart Helm de démonstration sur CPiN](https://github.com/cloud-pi-native/formation-cpin-deploiement)
5. ➡️ [Gestion des secrets sur CPiN](https://github.com/cloud-pi-native/formation-cpin-gestion-secret)
6. [Observabilité sur CPiN](https://github.com/cloud-pi-native/formation-cpin-observabilite)

## Présentation

Ce dépôt montre deux façons de gérer les secrets dans une approche GitOps sur CPiN :

- avec SOPS : [tutoriel SOPS](./sops/)
- avec Vault : [tutoriel Vault](./vault/)

> [!NOTE]
> SOPS vous permet de chiffrer un secret pour le versionner directement dans votre code d'infrastructure sans risquer de
> le rendre public. Vault vous permet de stocker vos secrets dans un coffre externe, d'où un opérateur Kubernetes les
> récupère pour le cluster. Dans les deux cas, un objet `Secret` Kubernetes est créé.

▶️ Suivez les deux TP pour vous familiariser avec ces concepts et terminer ce chapitre.

Une fois les deux TP terminés, vous pouvez passer à l'étape 6 :
[Observabilité sur CPiN](https://github.com/cloud-pi-native/formation-cpin-observabilite).
