# Phacet — tous les fichiers au même niveau

Ce dossier remplace le précédent paquet A-METTRE-SUR-GITHUB.
Il ne contient aucun sous-dossier ni fichier caché requis.

## Publier la branche de test sans fusionner dans main

1. Sur GitHub, sélectionner la branche **test-chapter**.
2. **Add file → Upload files** : glisser tous les fichiers de ce dossier, pas le dossier lui-même.
3. Valider le commit sur **test-chapter**.
4. **Settings → Pages → Source : Deploy from a branch**.
5. Sélectionner **test-chapter**, dossier **/ (root)**, puis **Save**.
6. Attendre la publication réussie et vérifier le lien **Visit site**.

Ne pas utiliser le workflow .github proposé précédemment. S’il a été ajouté entre-temps,
retirer .github/workflows/pages.yml de test-chapter avant cette publication.
Les anciens dossiers ouvert/ et documentation/ ne sont plus utilisés par cette version.

Cette méthode ne modifie ni ne fusionne main. GitHub Pages affiche toutefois la branche
sélectionnée à l’adresse du site : une éventuelle version déjà publiée à cette adresse
sera remplacée. Il n’y a pas de sous-chemin /test-chapter/ avec cette configuration.

## Adresses après publication

Livre fermé : https://sholy-klimb.github.io/phacet-livre-3d/
Livre ouvert : https://sholy-klimb.github.io/phacet-livre-3d/ouvert.html#chapitre-1

## WordPress

Copier embed-livre-ouvert.html dans un bloc HTML personnalisé autorisant les scripts.
Le livre est affiché seul sur fond transparent. Les CTA existants conservent leurs ID,
listés dans ID-CTA.md. Copier embed-livre-ferme.html pour le livre fermé.

## Fichiers

- index.html + livre.glb : livre fermé.
- ouvert.html + livre-ouvert.glb : livre ouvert.
- model-viewer.min.js : lecteur partagé.
- livre-ouvert.js + livre-ouvert.css : rendu et changement de double page.
- chapitres.js : correspondance entre ID et PNG.
- chapitre-01.png à chapitre-14.png : images originales, sans modification.
- wordpress-bridge.js : connexion entre les CTA WordPress et l’iframe.
- embed-livre-ouvert.html et embed-livre-ferme.html : exemples d’intégration.
- ID-CTA.md : liste des ID ; README.md : ces instructions.

Le chapitre 8 utilise chapitre-14.png ; le chapitre 9 utilise chapitre-13.png.
Aucun déploiement sur GitHub n’a été effectué depuis cette préparation locale.
Google model-viewer 4.1.0 : mentions de licence Apache-2.0 conservées dans son fichier.
