---
title: "Les trouvailles de juin"
date: 2020-07-05T20:14:34+02:00
draft: false
toc: true
comments: true
images:
tags:
  - trouvailles
---

Elles ont un peu de retard mais elles sont là ! C'est parti pour les découvertes du mois de juin. 

## Outils

Visual Studio Code a un ZenMode : c'est hyper agréable de naviguer, on peut passer d'un fichier ouvert à l'autre avec le raccourci Ctrl + Tab. 

## Liens chouettes

En cherchant les différences entre les objets `XMLHttpRequest` et `fetch`, je suis tombée sur ce blog très cool qui poste quasi quotidiennement des articles à propos de Javascript. 

[https://gomakethings.com/why-i-still-use-xhr-instead-of-the-fetch-api/](https://gomakethings.com/why-i-still-use-xhr-instead-of-the-fetch-api/) 

J'ai découvert cette API qui retourne des propriétés de plantes. Je l'ai trouvée via le repository d'APIs publiques utilisables pour des projets personnels ! 

https[://trefle.io/api/plants?q=rosemary](https://trefle.io/api/plants?q=rosemary) 

Mes moments de procrastination sur Twitter m'ont fait découvrir le super portfolio de Bruno Simon: [https://bruno-simon.com/](https://bruno-simon.com/) Mention spéciale aux Easter eggs. 

## CSS

Il est possible de rendre un sélecteur CSS case insensitive.  

{{<tweet 1275416501688942592>}}

## Javascript

Il est possible d'observer le changement de taille d'un élément en Javascript via l'API ResizeObserver. 

{{<tweet 1248899086490558465>}}

Il est possible de grouper les messages en console via la fonction console.group. 

{{<tweet 1191049744962842624>}}

Si vous ne suivez pas Addy Osmani, je vous le recommande vivement. Ses contenus sont toujours pertinents et applicables. 

J'ai découvert qu'on pouvait rendre un objet immutable grâce à la fonction `Object.freeze`. 

## DevOps

J'ai appris à supprimer les images Docker qui ne sont pas associées à un container.

`docker rmi $(docker images --filter "dangling=true" -q --no-trunc)`

J'ai aussi découvert comment lister les fichiers existants sur un volume Docker via busybox. 

[https://stackoverflow.com/questions/46866933/is-there-a-way-to-list-files-inside-a-docker-volume](https://stackoverflow.com/questions/46866933/is-there-a-way-to-list-files-inside-a-docker-volume)

## Fun

Le compte Twitter CuriositesJuridiques pour ses extraits ... insolites. 

{{<tweet 1278306074282557442>}}

C'est tout pour aujourd'hui ! 

N'hésitez pas à faire part de vos découvertes dans les commentaires :)
