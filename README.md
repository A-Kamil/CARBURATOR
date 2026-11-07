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
| Plafond hebdo | `Besoin / mois ÷ 4,33` |
| Ratio par jour | `Plafond hebdo ÷ Jours travaillés hebdo` |

Pour les véhicules électriques (par exemple le Citroën ë-Jumpy à 30 kWh/100 km), le même calcul donne des **kWh**. Ces kWh sont comptés à part des litres de carburant.

## Fonctionnalités

- **Import Excel** : chargez le fichier collaborateurs dans son format actuel. Les colonnes sont reconnues d'après leur titre : Nom, Prénom, Affectation, Type Véhicule, Adresse Ligne 1-3, CP, Ville, Distance Domicile-Magasin, Jours travaillés hebdo, Conso moyenne Véhicule, Distance parcourue par Jour en fonction du site, Jour de repos. Le fichier est lu dans le navigateur et n'est envoyé nulle part.
- **Fiche collaborateur** : elle montre le calcul étape par étape. La consommation se remplit d'après le véhicule et la tournée d'après le magasin.
- **Itinéraire Google Maps** : un bouton ouvre le trajet entre le domicile et le magasin, pour reporter ensuite la distance en km.
- **Référentiels modifiables** : types de véhicules (consommation, thermique ou électrique) et magasins (adresse, km de tournée par défaut).
- **Synthèse** : km, litres, kWh et coût estimé par mois, avec un filtre par magasin et un filtre par statut (complet ou à compléter).
- **Export Excel** : les formules restent actives dans le fichier exporté, avec un onglet de synthèse par magasin. On peut aussi copier le tableau pour le coller directement dans Excel.

Les données saisies restent dans le navigateur (`localStorage`). Pour les transmettre, utilisez l'export Excel.

## Données personnelles

Le dépôt est public. Les fichiers collaborateurs (`.xlsx`, `.csv`) sont exclus par `.gitignore` : ils contiennent des adresses et des numéros de téléphone et ne doivent pas être versionnés. Les 5 collaborateurs affichés au premier lancement sont fictifs.

## Publier avec GitHub Pages

Dans *Settings → Pages*, choisissez *Deploy from a branch*, puis la branche `main` et le dossier `/ (root)`.
