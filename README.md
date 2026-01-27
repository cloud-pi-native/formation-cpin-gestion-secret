# Gestion des secrets sur CPIN

Vous en êtes à l'étape 5 de la formation CPiN :
1. [Gestion des projets CPiN](https://github.com/cloud-pi-native/formation-cpin-gestion-projet)
2. [Application d'exemple pour déploiement sur CPiN](https://github.com/cloud-pi-native/formation-cpin-repo-applicatif)
3. [Gestion des artefacts sur CPiN](https://github.com/cloud-pi-native/formation-cpin-harbor-trivy)
4. [Chart Helm de démonstration sur CPiN](https://github.com/cloud-pi-native/formation-cpin-deploiement)
5. ➡️ [Gestion des secrets sur CPIN](https://github.com/cloud-pi-native/formation-cpin-gestion-secret)
6. [Observabilité sur CPiN](https://github.com/cloud-pi-native/formation-cpin-observabilite)

## Présentation

Ce dépôt montre comment gérer les secrets dans une approche GitOps sur CPiN de deux façons différentes : 

 - Via Mozilla SOPS : [tutorial SOPS](./sops/)
 - Via Vault : [tutorial Vault](./vault/)

> [!NOTE]
> SOPS vous permet de chiffrer un secret pour l'embarquer directement dans votre code d'infrastructure sans prendre le 
> risque de le rendre publique. Vault vous permet de vous reposer sur un opérateur tiers pour stocker vos secrets et de 
> les faire récupérer par le cluster. Dans les deux cas, un objet *secret* Kubernetes sera créé.

▶️ Suivez les deux TPs afin de vous familiariser avec ces concepts et compléter ce chapitre. 