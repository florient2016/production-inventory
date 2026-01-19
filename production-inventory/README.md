# Ansible Inventory (AAP 2.6)

Ce depot contient un inventaire Ansible (YAML) maintenable et pret pour AAP 2.6.

## Contenu
- `inventory.yaml` : structure des groupes et declaration des hotes
- `group_vars/` : variables par groupes (OS, env, dept, site, cloud)
- `host_vars/` : variables specifiques a certains hotes

## Utilisation dans AAP 2.6
1. Creer une Credential "Source Control" et referencer ce repo Git.
2. Creer un Project base sur ce repo (SCM).
3. Creer un Inventory -> Sources -> Source: "Sourced from a Project".
4. Indiquer le chemin de l'inventaire : `inventory.yaml`.
5. Sync.

## Exemples de ciblage
- Tous les PROD : `-l env_prod`
- Windows en preprod : `-l env_preprod:&windows`
- Finance DEV Linux : `-l finance_dev_linux`
- Tout Cloud AWS : `-l site_cloud:&cloud_aws`

## Notes
- Les variables sont separees dans `group_vars/` (bonne pratique), l'inventaire reste lisible.
- Dupliquer les patterns de groupes "leaf" pour atteindre 50+ hotes.
