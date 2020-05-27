---
title: Débuter avec Mongo DB
date: "2016-11-10T09:01:20+00:00"
description: "Une cheatsheet des commandes dont j'ai eu besoin lorsque j'ai débuté avec MongoDB."
template: post
slug: /fr/debuter-avec-mongo-db/
category: Cheatsheets
tags:
  - cheat sheet
  - mongo
---
## Démarrer Mongo

```mongod```

## Démarrer Mongo sans les journaux

```mongod --nojournal```

Peut être pratique si vous n&rsquo;avez pas beaucoup d&rsquo;espace sur votre ordi.

## Se connecter en Shell à Mongo

```mongo```

&nbsp;

## Créer une base de données

```use <nom_de_la_base_de_données>```

Il faut y enregistrer au moins un document pour que la base de données soit vraiment sauvegardée.

## Créer un utilisateur

```db.createUser(
{
  user: "fashion",
  pwd: "fashion",
  roles: [ "readWrite", "dbAdmin" ]
});
```

## Voir le contenu d&rsquo;une collection

```db.nom_collection.find();```

Une collection Mongo s&rsquo;apparente à une table MySQL et un document Mongo s&rsquo;apparente à l&rsquo;entrée d&rsquo;une table MySQL.

show all content collection: http://stackoverflow.com/questions/24985684/mongodb-show-all-contents-from-all-collections
