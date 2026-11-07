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

## Fonctionnalités

- **Chiffres clés** : besoin en carburant (L) et en électricité (kWh) par mois et par semaine, km et coût estimé. Ils suivent les filtres appliqués.
- **Répartition par magasin** : en litres, kWh ou km, par mois ou par semaine. Cliquer sur un magasin filtre la liste.
- **Import Excel** : par bouton ou en glissant le fichier sur la page. Le fichier collaborateurs est accepté dans son format actuel, et le résumé indique les fiches à compléter ainsi que les nouveaux véhicules et magasins. L'import peut être annulé. Le fichier est lu dans le navigateur et n'est envoyé nulle part.
- **Compléter les fiches** : ce bouton enchaîne les fiches incomplètes l'une après l'autre. Les champs manquants sont surlignés.
- **Fiche collaborateur** : elle montre le résultat, la journée type (aller, retour, tournée) et la formule appliquée. La consommation se remplit d'après le véhicule et la tournée d'après le magasin.
- **Itinéraire Google Maps** : un bouton ouvre le trajet entre le domicile et le magasin, pour reporter ensuite la distance en km.
- **Liste** : besoin par mois, par semaine et par jour pour chaque collaborateur. Recherche (touche `/`), filtres par magasin, par statut et par énergie (carburant ou électricité), tri par colonne. Sur téléphone, la liste s'affiche en cartes.
- **Référentiels modifiables** : véhicules et magasins. Quand une valeur par défaut change, on peut l'appliquer à tous les collaborateurs concernés.
- **Annulation** : une suppression ou un import peut être annulé.
- **Export Excel** : les formules restent actives dans le fichier exporté, avec un onglet de synthèse par magasin (par mois et par semaine). L'export suit les filtres en cours, par exemple uniquement les véhicules électriques. On peut aussi copier le tableau pour le coller dans Excel.

Les données saisies restent dans le navigateur (`localStorage`). Pour les transmettre, utilisez l'export Excel.

## Données personnelles

Le dépôt est public. Les fichiers collaborateurs (`.xlsx`, `.csv`) sont exclus par `.gitignore` : ils contiennent des adresses et des numéros de téléphone et ne doivent pas être versionnés. Les 5 collaborateurs affichés au premier lancement sont fictifs.

## Publier avec GitHub Pages

Dans *Settings → Pages*, choisissez *Deploy from a branch*, puis la branche `main` et le dossier `/ (root)`.
