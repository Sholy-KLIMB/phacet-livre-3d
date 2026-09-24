# Phacet — version de test sans fusion dans main

Ce dossier doit être déposé à la racine de la branche **test-chapter**.
Ne pas le déposer sur main et ne pas créer de sous-dossier A-METTRE-SUR-GITHUB dans le dépôt.

## Activer la publication de test

1. Dans le dépôt GitHub, ouvrir **Settings → Pages**.
2. Choisir **GitHub Actions** dans **Build and deployment → Source**.
   Ne pas sélectionner « Deploy from a branch » pour cette configuration.
3. Déposer le contenu de ce dossier sur la branche **test-chapter**, y compris
   les dossiers **.github/** et **ouvert/**. Sur Mac, Cmd + Maj + . affiche les
   fichiers et dossiers cachés dans le Finder.
4. Après le commit, ouvrir l’onglet **Actions** et attendre la réussite de
   **Publier la version de test du livre**.
5. Si le déploiement est bloqué par les règles d’environnement : dans
   **Settings → Environments → github-pages → Deployment branches and tags**,
   autoriser explicitement **test-chapter**. Conserver les protections existantes.
   Relancer ensuite le déploiement bloqué.

Si les fichiers ont été ajoutés avant l’activation de Pages, relancer le workflow
échoué depuis Actions, ou faire un nouveau commit sur test-chapter.
Le premier lancement se fait automatiquement au push ; le bouton de lancement
manuel peut ne pas apparaître tant que le workflow n’est pas dans la branche par défaut.

## Adresses de test après un déploiement réussi

- Livre fermé : https://sholy-klimb.github.io/phacet-livre-3d/test-chapter/
- Livre ouvert : https://sholy-klimb.github.io/phacet-livre-3d/test-chapter/ouvert/#chapitre-1

Ces adresses ne fonctionneront qu’après activation de Pages et réussite du workflow.

## Fonctionnement

GitHub Pages publie un seul site par dépôt. Le workflow prépare donc un site combiné :

- `/` contient les fichiers du livre lus depuis **main** ;
- `/test-chapter/` contient les fichiers lus depuis **test-chapter**.

Chaque push sur test-chapter reconstruit ces deux chemins. La publication utilise
les fichiers de main présents lors du lancement, sans écrire sur cette branche.
Aucune fusion, aucun commit dans main et aucune modification des CTA de production
ne sont effectués par le workflow. Le site Pages est publié en entier à chaque
exécution ; les deux versions sont donc toujours incluses ensemble.
Le workflow est limité aux exécutions sur test-chapter. Un push sur main seul ne
le déclenche pas. La publication automatique de production sera à configurer
séparément quand la version de test sera validée.

## Embed WordPress de test

Utiliser **documentation/embed-test-livre-ouvert.html** pour le livre ouvert.
Utiliser **documentation/embed-test-livre-ferme.html** pour le livre fermé.
Ces fichiers pointent vers /test-chapter/, y compris le script des CTA.
Les ID restent identiques : cta-chapitre-1 à cta-chapitre-9, etc.
La liste complète est dans documentation/INTEGRATION.md.
Les fichiers embed-livre-ouvert.html et embed-livre-ferme.html restent les exemples
pour les adresses principales ; ne pas les utiliser pour tester cette branche.

## Contenu indispensable

- `.github/workflows/pages.yml` : publication automatisée.
- `.github/scripts/prepare_pages.py` : assemble main et test-chapter et vérifie les fichiers.
- `index.html`, `livre.glb`, `model-viewer.min.js` : livre fermé et lecteur partagé.
- `ouvert/` : modèle ouvert, scripts et 14 PNG originaux.
- `.nojekyll` : configuration Pages.
- `documentation/` : embeds et ID.

Le workflow ne publie pas les sauvegardes, tests, archives ou dossiers .github.
Un fichier indispensable manquant fait échouer la préparation avant tout déploiement.
Il utilise les actions officielles décrites dans la documentation GitHub :
https://docs.github.com/en/get-started/start-your-journey/deploying-your-website-automatically

## Vérification locale réalisée

Préparation testée avec les fichiers publics actuels de main : contenu principal
identique octet pour octet, version de test isolée, 14 PNG présents, références HTML
résolues, et échec contrôlé en cas de dossier ouvert manquant.
Le workflow n’a pas encore été exécuté sur votre compte GitHub.

Google model-viewer 4.1.0, Apache-2.0 : mentions du lecteur conservées dans son fichier.
