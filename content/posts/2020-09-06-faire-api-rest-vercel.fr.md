---
title: "Faire une API Rest avec Vercel"
date: 2020-09-06T20:13:37+02:00
draft: false
toc: true
comments: true
cover: "img/clouds.jpeg"
images: 
tags:
  - hack-days
---

[*Cover picture by Tomasz Sroka*](https://unsplash.com/photos/A4AJVLFu-Ug)

Vercel (*anciennement Zeit*) est une plateforme JAMStack qui permet de déployer facilement des applications à partir d'un repository Git distant. Le service fourni est similaire à celui de Netlify, l'objectif est d'améliorer l'expérience de développement et faciliter les déploiements.

On peut héberger des applications (un blog Gatsby par exemple!) mais aussi des fonctions Serverless. [Une fonction Serverless](https://serverless-stack.com/chapters/fr/what-is-serverless.html) est une fonction qui est exécutée à la demande (lors de la réception d'une requête HTTP par exemple) par un service de Cloud tiers (AWS Lambda, Cloud Functions...) : on ne paie donc pas un nombre de serveurs mais plutôt à l'usage des fonctions. 

J'ai voulu tester en créant une API très simple qui retourne une citation aléatoire de Jul (*jugez moi*). 

Ces citations sont stockées dans une collection sur une base MongoDB.  

## Pré-requis

Avant toute chose, j'ai installé [vercel-cli](https://vercel.com/download), qui permet de gérer les déploiements mais aussi de démarrer un environnement local similaire à la production, ce qui est bien pratique pour éviter les mauvaises surprises

## Création d'une base de données

Il est possible de créer une petite base [MongoDB gratuite](http://cloud.mongodb.com/) sur le cloud, parfaite pour une sandbox.  Il est possible de créer des secrets sur Vercel très facilement à l'aide de la commande 

```bash
vercel secrets add "NOM_DU_SECRET VALEUR"
```

*On oublie pas les quotes !*

## Création de l'application

Vercel impose une structure dans la manière de déclarer sa fonction serverless. Il faut que la fonction se trouve dans un dossier api. 

Il suffit de démarrer son environnement local à l'aide de la commande vercel dev. 

J'ai choisi d'utiliser Node.js pour mon API mais il est possible d'utiliser Go, Python ou Ruby également. [La documentation est exhaustive](https://vercel.com/guides) sur la manière de démarrer un projet dans différentes technos. 

## Bilan

Le setup de l'environnement local est très agréable. Il vient même avec un hot-reload, l'expérience de développement est painless. Les commandes de Vercel ressemblaient à celles de Kubernetes ce qui m'a moins mêlée. 

Attention si vous utilisez Docker en parallèle, il est possible que Vercel conflicte avec des ports déjà en usage. Pensez à stopper les applications (je n'ai pas trouvé de moyen de faire démarrer Vercel sur un autre port). 

J'aurais du mal à utiliser un service de ce type sur un projet réel. J'ai l'impression que ça s'adapte plutôt bien pour des mini-projets de test ou des proof of concepts mais que les prix peuvent rapidement s'envoler dans un contexte de production normal. 

En tout cas, je recommande l'outil pour tous ceux qui souhaiteraient construire un portfolio sur leurs projets open source ! 

## Ressources

- [https://vercel.com/guides/deploying-a-mongodb-powered-api-with-node-and-vercel](https://vercel.com/guides/deploying-a-mongodb-powered-api-with-node-and-vercel)
- [https://www.lambrospetrou.com/articles/battle-of-jamstack-platforms-netlify-vercel-aws/](https://www.lambrospetrou.com/articles/battle-of-jamstack-platforms-netlify-vercel-aws/)
- [https://jamstack.org/](https://jamstack.org/)