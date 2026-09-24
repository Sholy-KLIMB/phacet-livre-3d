# Livre 3D Phacet : version sans zoom

Livre seul, fond transparent, rotation au glisser conservée.
Zoom du modèle désactivé (molette et pincement), sans boutons, sommaire ni barre de chargement.

## Version amincie — 24 septembre 2026

Dimensions du modèle : 210,5 × 298 × 13,5 mm (épaisseur précédente : 36 mm).
Réduction de l’épaisseur : 62,5 %. La largeur et la hauteur sont conservées.
Les trois PNG fournis sont intégrés à leur résolution originale, sans réencodage.
Les proportions 1684/2384 des couvertures et 108/2384 de la tranche sont
respectées par le placement des images sur les faces ; les bords restent biseautés.
Le modèle original est conservé dans sauvegarde/livre-original.glb, hors du paquet à publier.

Pour mettre à jour le site existant, remplacer livre.glb et index.html sur GitHub.
La référence du modèle dans index.html est versionnée pour éviter l’ancien cache.
L’iframe WordPress existante peut rester identique si elle pointe vers ce même site.
Le fichier embed-wordpress.html contient également le code pour un bloc HTML personnalisé.
Cette modification est locale : aucune publication GitHub ou WordPress n’a été effectuée.

## Upload GitHub

Dézipper le paquet et déposer son contenu à la racine de Sholy-KLIMB/phacet-livre-3d. Ne pas déposer le ZIP lui-même.
Fichiers nécessaires : index.html, livre.glb, model-viewer.min.js. Le fichier .nojekyll est fourni pour désactiver Jekyll.

Dans Settings > Pages : Deploy from a branch, main, /(root), Save.
Attendre la publication réussie, puis vérifier Visit site.
Adresse prévue : https://sholy-klimb.github.io/phacet-livre-3d/
Ce paquet ne confirme pas que GitHub Pages est déjà activé ou publié.

## Webflow

Copier le contenu de embed-webflow.html dans un bloc Code Embed, après confirmation de l'adresse publiée.

Lecteur Google model-viewer 4.1.0, Apache-2.0. Mentions de licence conservées dans le fichier JavaScript.

## Livre ouvert et sélection des doubles pages

La version ouverte est dans `ouvert/`. Voir `ouvert/INTEGRATION.md` pour les 14 ID,
les raccourcis de chapitres et le branchement des boutons WordPress.
`ouvert/index.html` affiche uniquement le modèle 3D, sans interface.
`ouvert/demo.html` redirige vers ce lecteur. Les ID des CTA sont dans le guide.
`embed-wordpress-ouvert.html` contient le code à intégrer sur WordPress.
Le paquet `phacet-livre-ouvert.zip` est séparé du livre fermé.
