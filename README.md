# Gestion des données produits — BottleNeck

Rapprochement et analyse des données produits d'un marchand de vin, pour
fiabiliser le pilotage du chiffre d'affaires et des stocks.

---

## Contexte / besoin métier

BottleNeck, marchand de vin, utilise des outils artisanaux et plusieurs
extractions disjointes pour suivre son activité : ERP (prix, stock),
site web (ventes), et une table de liaison
entre les deux référentiels. 

## Données

- **Source** : 3 exports — ERP (référence, prix, stock), site web (SKU,
  quantités vendues, description produits), table de liaison ERP ↔ Web
- **Qualité** : référentiels non alignés entre les systèmes, table de liaison
  mise à jour par un stagiaire pour les nouveaux produits
- **Limites** : au moins 8 erreurs identifiées dans les données (saisie,
  type, calcul, jointure) à corriger avant analyse

## Démarche

1. **Rapprochement** des trois sources via la table de liaison (Python)
2. **Détection et correction des erreurs** : erreurs de saisie, de type,
   de calcul, de jointure
5. **Détection des valeurs aberrantes** : Z-score et écart interquartile,
   boxplot pour visualiser les anomalies de prix
6. **Analyse stock** : état des stocks, taux de marge, rotation, nombre de
   mois de stock
7. **Analyse de corrélation** entre variables quantitatives (prix, prix
   d'achat, stock, ventes, prix HT, taux de marge)

## Résultats

- Base de données produits fiabilisée après correction des erreurs identifiées
- Chiffre d'affaires calculé par produit et au global
- Identification des références clés et des anomalies de prix
- Recommandations sur la fiabilisation des référentiels ERP / site web

## Limites & pistes

- Correction manuelle des erreurs, pas de contrôle automatique à la source
- Table de liaison dépendante d'une mise à jour manuelle
- **Pistes** : mettre en place des contrôles de cohérence automatisés à
  l'import, unifier les référentiels produits, suivre les indicateurs de
  stock et de marge de façon récurrente
