# Contribuer à Mboa

Ce guide s'applique à tous les dépôts de l'organisation `mboacm`.

## Flux de travail

1. Créer une branche depuis `main` : `feature/M10-annonces`, `fix/M12-notification`, `chore/ci` (le préfixe `M..` est le module du CDC, Doc 10).
2. Faire des commits courts au format *Conventional Commits* : `feat(M10): création d'annonce`, `fix(M12): file d'attente hors ligne`, `chore(ci): cache Maven`.
3. Ouvrir une pull request vers `main` avec le modèle fourni. Lier l'issue correspondante.
4. Attendre que la CI (`ci`) soit verte et qu'une revue soit approuvée.
5. Fusionner par **squash**. Ne jamais pousser directement sur `main`.

`main` déploie l'environnement de **staging**. Un tag `vX.Y.Z` déploie la **production** après approbation d'un propriétaire.

## Règles

- **Aucun secret dans le dépôt** : clés d'API, mots de passe, jetons, certificats. Ils vivent dans les secrets GitHub ou sur le serveur. Un secret poussé par erreur est considéré comme compromis et doit être renouvelé.
- **Rétrocompatibilité des migrations** : une migration Flyway déjà fusionnée n'est jamais modifiée ; on en ajoute une nouvelle.
- **Backend d'abord** : une fonctionnalité est spécifiée et testée côté API (Swagger / Postman) avant son intégration côté Flutter.
- **Tests** : toute règle métier du CDC (RM-Mxx-yy) touchée est couverte par un test.
- **Texte et libellés** : français, sans SMS comme canal (RG-09), avec les badges « Titre vérifié » et « Vérifié sur place ».
- **Données personnelles** : aucune donnée réelle dans les jeux de test, les captures ou les journaux.

## Revue

Le fondateur revoit les pull requests qui touchent aux migrations, aux paiements, à l'authentification, aux workflows et aux fichiers de sécurité (`CODEOWNERS`).
