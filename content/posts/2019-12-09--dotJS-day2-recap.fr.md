---
title: Une journée à dotJS (Jour Backend 2)
date: "2019-12-09T19:23:42+00:00"
description: Débrief de la conférence dotJS Jour 2 à Paris en décembre 2019
template: post
draft: false
slug: /fr/recapitulatif-dotJS-jour2-decembre-2019
category: Conférences
tags:
  - conferences
  - javascript
---

# Récapitulatif - dotJS 2019 

J'ai eu la chance d'assister à dotJS cette année grâce à des places qui ont été offertes par les dotConferences à la communauté <a href="https://paris.ladiesofcode.com/" target="_blank">Ladies of Code</a>. 

<a href="https://twitter.com/Jawache">@Jawache</a> a pris la parole sur notre impact environnemental en tant que développeur. L'électricité est responsable à 30% des émissions de CO2. On ne peut se permettre d'en gaspiller. 
Google Cloud serait un cloud Carbone neutral (ça m'étonne un peu).
Les servers produisent du carbone, on pollue moins avec le serverless.

Le serverless présente aussi des avantages économiques

- Autoscaling 
- On paie selon la durée et la consommation mémoire des fonctions que l'on exécute.


```
Nitr.ooo fireship.io = gcp functions nest.js
```

Si le sujet vous intéresse, consulter climateaction.tech pour s'impliquer plus.

__________________

<a href="https://twitter.com/devdevcharlie">@devdevcharlie</a> nous a montré les possibilités de recognition de sounds en exploitant la WebAudio API en javascript et le Machine Learning (avec TensorFlow). La WebAudio API récupère les données du microphone.

Sa démo présente un spectrogramme (la photo d'un son). Plus le son est fort, plus la couleur sur l'amplitude du spectrogramme est lumineuse.

Gather data from WEBAUDIOAPI and transforme it for tensorflow. Multidimensionnel array with labels for pattern recognition. La démo est accessible <a href="https://acoustic-ml.netlify.com">ici</a>, et c'est plutôt impressionnant : acoustic-ml.netlify.com

__________________

<a href="http://www.twitter.com/BertBelder">BertBelder</a> nous a présenté Deno, un runtime for JavaScript and Typesvript (webassembly) qui vise à résoudre les soucis que Node pose. Il utilise V8, Rust, Tokio (event.loop), TypeScript.

Node a un système de modules complexes, exposé aux failles et il existe un tas de tooling parallèle là où Deno a une API web et un tooling intégré.

_______

Quelques talks qui m'ont été recommandés en discutant durant les breaks: <a href="https://www.youtube.com/watch?v=qTHGmVrOGZo">Universe in a single arrow</a> et <a href="https://www.youtube.com/watch?v=yJDv-zdhzMY">Mother of all demos</a> (la première démonstration d'une souris, d'un clavier pour les amateurs d'images d'archive).


_______

@stefanjudis a donné un lightning talk super sur les expressions régulières. <a href="https://speakerdeck.com/stefanjudis/regular-expressions-my-secret-love">Les slides sont claires</a>, je vous recommande de les checker, une bonne piqûre de rappel pour les humains nuls en regexp comme moi ^_^

```
?: Omit captions group
?<rest> capture group
\p{Emoji} capture emoji 
```
_______

<a href="https://twitter.com/vladikoff">Vlad Filippov</a> a donné un talk sur <a href="https://docs.google.com/presentation/d/1vunpCYP3ggD7Sfp6Zhvu9fm9DqEt2jsCDPHo93Va0HU/edit">WebAssembly</a> (wasm).
C'est un nouveau language bas niveau, similaire à l'assembleur, conçu pour compléter des applications web javascript. On peut charger des modules WebAssembly dans des applications Javascript : certaines bibliothèques l'utilisent déjà comme pica. 

L'objectif est d'améliorer les performances. Attention cependant aux cas d'application: il faut toujours benchmarker les gains et être vigilant sur la taille du module WASP. 

WebAssembly.studio

_____

<a href="https://twitter.com/mourner">Vladimir Agafonkin</a> (créateur de Leaflet) a donné un talk sur l'optimisation d'algorithmes. 

Il a présenté le cas d'une bibliothèque Delaunay qui a subi plusieurs optimisations sur des modules npm. ( delaunay-fast // faster-delaunay // delaunator étant le plus rapide)

Étapes pour optimiser un algorithme:
- Trouver le bottleneck (parties les plus longues) grâce à des outils de profiling (on sous-utilise celui de Chrome).
- Le code lent est du code pas nécessaire
- Être vigilant sur les complexités, faire varier le code selon les tailles d'input.

```
O(n) loop 
O(n2) o(n3) boucles imbriquées
```

Attention aux fonctions natives Javascript (Array.indexOf, etc.) qui ont aussi leur propre complexité (assez grosse).

accidentallyquadratic.tumblr.com

Memory complexity _ allocate Much memory than we need 
Ces fonctions : `slice concat Map filter split` utilisent plus de  mémoire que nécessaire.

O.log(n) best complexity.
Binary search.

Astuce d'optimisation: Trier les données en entrer pour processer les données plus rapidement. En faire plus au début (tri) pour en faire moins après. 

HashTable -> Array peut faire gagner en performance. 

1. Learn how things work under the wood ! Surtout dans les fonctions JS par défaut qu'on a  l'habitude d'utiliser.
2. Tout peut être amélioré ! 

________

<a href="https://twitter.com/jlongster">James Long</a>, créateur de Prettier, a donné un talk sur la synchronisation des données sur des applications distribuées. 

Il y a parlé de la complexité de la synchronisation d'applications hors-ligne et notamment la garance de la consistance des données. 

Un point critique est l'ordre de réception des données: utiliser un timestamp pour réordonner les datas (Vector clock, Hybrid logical clock). 
Un timestamp existe par device et est généré / assigné à un changement émis.

Il faut trouver des solutions les plus simples possible pour garantir la fiabilité dans un système distribué. 

Les slides sont disponibles <a href="https://jlongster.com/s/dotjs-crdt-slides.pdf">par ici</a>.
____

<a href="https://www.twitter.com/nodebotanist">@nodebotanist</a> nous a joué un son de guitare connecté à une application Node qui changeait la couleur d'une LED branchée à sa guitare. Le tout réalisé avec des bibliothèques npm suivantes: midi tonal color ws (websocket). 

@nodebotanist a aussi mis au défit les recruteurs présents de recruter quelqu'un de différent d'eux.

______

@maggiepint a présenté la nouvelle librairie Temporal qui vise à résoudre les soucis actuels de Date en Javascript. (Months index from 0, Mutability, Timezone gaps, No date only représentation).

_____

<a href="https://www.twitter.com/littledan">Daniel Ehrenberg</a> a ensuite présenté TC39, une communauté de développeurs qui améliorent Javascript et comment nous pouvons les aider.  

tc39.es

```
# is the new _ for strong encapsulation.
```


J'ai passé deux jours très enrichissants et plein de découvertes / belles rencontres. J'espère pouvoir renouveler l'expérience l'an prochain ! :) 