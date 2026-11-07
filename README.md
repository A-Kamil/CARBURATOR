# CARBURATOR

Calcul du besoin carburant par collaborateur, à partir de son domicile, du magasin où il travaille, du véhicule utilisé et des kilomètres de tournée.

Tout tient dans une seule page : `index.html`. Ouvrez-la dans un navigateur ou publiez-la avec GitHub Pages. Il n'y a ni serveur ni installation.

## Méthode de calcul

Ce sont les mêmes formules que dans le fichier Excel `besoin_carburant.xlsx` :

| Étape | Formule |
|---|---|
| Km par jour | `Distance Domicile-Magasin × 2 + Distance parcourue par jour (tournée du site)` |
| Distance totale / mois | `Km par jour × Jours travaillés hebdo × 4,33` |
| Besoin carburant / mois | `Distance totale / mois × Conso moyenne véhicule ÷ 100` |
| Besoin / semaine (plafond hebdo) | `Besoin / mois ÷ 4,33`, soit `Km par jour × Jours travaillés hebdo × Conso ÷ 100` |
| Besoin par jour (ratio) | `Besoin / semaine ÷ Jours travaillés hebdo` |

Pour les véhicules électriques (par exemple le Citroën ë-Jumpy à 30 kWh/100 km), le même calcul donne des **kWh**. Ces kWh sont comptés à part des litres de carburant.

### Semaine avec jour férié

La semaine de travail va du lundi au samedi : un collaborateur travaille tous les jours sauf ses jours de repos. Si le jour férié n'est pas un de ses jours de repos, son besoin de la semaine devient `Besoin / semaine × (Jours travaillés − 1) ÷ Jours travaillés`. Exemple : 38,8 L × 3 ÷ 4 = 29,1 L, soit 9,7 L de moins sur la carte. Les plannings variables (« Aléatoire ») ou incomplets sont listés à part, à vérifier.

## Fonctionnalités

- **Chiffres clés** : besoin en carburant (L) et en électricité (kWh) par mois et par semaine, km et coût estimé. Ils suivent les filtres appliqués.
- **Répartition par magasin** : en litres, kWh ou km, par mois ou par semaine. Cliquer sur un magasin filtre la liste.
- **Import Excel** : par bouton ou en glissant le fichier sur la page. Le fichier collaborateurs est accepté dans son format actuel, et le résumé indique les fiches à compléter ainsi que les nouveaux véhicules et magasins. Le n° de carte carburant (colonne « N° Carte ») est repris. L'import peut être annulé. Le fichier est lu dans le navigateur et n'est envoyé nulle part.
- **Compléter les fiches** : ce bouton enchaîne les fiches incomplètes l'une après l'autre. Les champs manquants sont surlignés.
- **Fiche collaborateur** : elle montre le résultat, la journée type (aller, retour, tournée) et la formule appliquée. La consommation se remplit d'après le véhicule et la tournée d'après le magasin.
- **Itinéraire Google Maps** : un bouton ouvre le trajet entre le domicile et le magasin, pour reporter ensuite la distance en km.
- **Liste** : besoin par mois, par semaine et par jour pour chaque collaborateur. Recherche (touche `/`), filtres par magasin, par statut, par énergie (carburant ou électricité) et par jour travaillé (« Travaille le mercredi »), tri par colonne. Sur téléphone, la liste s'affiche en cartes.
- **Jours fériés** : choisissez un jour férié (calculés automatiquement, Pâques, Ascension et Pentecôte compris) ou une autre date. L'outil liste les collaborateurs qui travaillent ce jour-là, avec leur n° de carte, le besoin de la semaine normale, celui de la semaine fériée et la baisse à appliquer sur la carte. Les plannings variables ou incomplets sont mis à part, à vérifier. La liste s'exporte en Excel.
- **Référentiels modifiables** : véhicules et magasins. Quand une valeur par défaut change, on peut l'appliquer à tous les collaborateurs concernés.
- **Annulation** : une suppression ou un import peut être annulé.
- **Export Excel** : les formules restent actives dans le fichier exporté, avec un onglet de synthèse par magasin (par mois et par semaine). L'export suit les filtres en cours, par exemple uniquement les véhicules électriques. On peut aussi copier le tableau pour le coller dans Excel.

Les données saisies restent dans le navigateur (`localStorage`). Pour les transmettre, utilisez l'export Excel.

## Données personnelles

Le dépôt est public. Les fichiers collaborateurs (`.xlsx`, `.csv`) sont exclus par `.gitignore` : ils contiennent des adresses et des numéros de téléphone et ne doivent pas être versionnés. Les 5 collaborateurs affichés au premier lancement sont fictifs.

## Publier avec GitHub Pages

Dans *Settings → Pages*, choisissez *Deploy from a branch*, puis la branche `main` et le dossier `/ (root)`.
