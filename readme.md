# Vue3 - ECF - DWWM - Décembre 2024
 

Objectif: partir d'une maquette statique et faire un projet vue3 qui sollicite une api externe
Merci d'utiliser les notions vues en classe 
# Le front

  
```sh
npm init vue@latest nom-prenom-vue3
> cd  <nom-prenom-vue3>  > npm install  > npm run dev
```
  

Installez toutes les dépendances nécessaires pour avoir une vue au plus près de la maquette html/css

  

Découpez ensuite votre projet en composants

  

  

> Sur l'index vous pouvez par exemple choisir d'afficher 3 amiibo au
> hasard ou vos trois amiibo préférés

> Sur la page avec le tableau merci d'afficher 10 amiibos maximun
> Il est possible d'afficher plus d'amiibos via un bouton 
  

  

# L'api

  

  

L'api publique permet de récupérer des infos sur des "amiibo", des petites figurines Nintendo.

  

[La documentation de l'api](https://www.amiiboapi.com/docs/)

  

  

Il y a deux endpoints importants: récupérer une liste d'amiibo et récupérer les détails d'un amiibo

  

  

**Récupérer tous les amiibos**

  

[https://www.amiiboapi.com/api/amiibo/](https://www.amiiboapi.com/api/amiibo/)

  

  

📌L'id des amiibo est le "tail"

  

[https://www.amiiboapi.com/api/amiibo/?tail=01610502](https://www.amiiboapi.com/api/amiibo/?tail=01610502)

  

  

## Grille

- Import des assets statics

- Gestion des routes

- Découpage composants

- Récupération data from api

- Affichage des données de l'api

- Nommage, clean code, logique

  

**Rendu**

L'adresse du repo sous cette forme **nom-prenom-vue3**.git

Durée: **3h**

> [!WARNING]
> Il vaut mieux un petit projet qui build qu'un gros qui build pas