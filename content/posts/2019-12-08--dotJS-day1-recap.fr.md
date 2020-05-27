---
title: Une journée à dotJS (Jour Frontend 1)
date: "2019-12-08T19:23:42+00:00"
description: Débrief de la conférence dotJS à Paris en décembre 2019
template: post
draft: false
slug: /fr/recapitulatif-dotJS-jour1-decembre-2019
category: Conférences
tags:
  - conferences
  - javascript
---

# Récapitulatif - dotJS 2019 

J'ai eu la chance d'assister à dotJS cette année grâce à des places qui ont été offertes par les dotConferences à la communauté <a href="https://paris.ladiesofcode.com/" target="_blank">Ladies of Code</a>. 

En discutant avec quelques personnes, j'y ai appris l'existence d'un framework Node.js, <a href="https://docs.nestjs.com/">Nest.js</a> qui permettrait d'avoir une application plus structurée qu'une app Node classique qui n'utiliserait qu'Express pour le routing.

<a href="https://twitter.com/posva">Eduardo San Martin Morote</a> a donné un talk plutôt sympa intitulé Modern Front-end Routing. Il y a décortiqué l'API History en évoquant la complexité entre les différents navigateurs (UrlSearchParams notamment mal supporté par IE et Safari). Les navigateurs encodent les caractères spéciaux dans une URL différement et leur récupération via les API disponibles en JS en est affectée. L'encodage des URLs est donc recommandé (même si ce n'est pas "joli"). 
```
EncodeURI //path and hash
DecodeURI //Path and hash
EncodeURIComponent //Query keys only
```
Ses slides sont disponibles <a href="https://modern-frontend-routing-dot19.netlify.com/assets/player/keynotedhtmlplayer" target="_blank">ici</a>.

S'en est suivi un talk "Complexity in Simplicity" chouette donné par <a href="https://twitter.com/NikkitaFTW">Sara Viera</a> où j'y ai appris des fun-facts tels que: 
- les placeholders ne sont pas traduits automatiquement par le navigateur
- les placeholders ne sont pas lu par les technologies VoiceOver, d'où l'utilité des labels
- On peut récupérer le language du navigateur via un objet `navigator.language`


Ses slides sont très claires et <a href="https://complexity-in-simplicity.surge.sh/">par ici</a>. Une phrase choc de ce talk :

> Your pretty code won't make your users come back

Côté lightning talks, il y a eu:
- une présentation dense mais qui donnait envie de <a href="https://breeze.github.io/doc-js/">Breeze</a> un ORM pour applications Javascript. 
- une présentation de Svelte.js comparé à React et Vue.
- une bibliothèque de test côté front, <a href="https://testing-library.com/docs/dom-testing-library/intro">DOM Testing Library</a>

Ce dernier talk était particulièrement intéressant et m'a donné envie d'y jeter un oeil. Il y a possibilité de simuler le click sur un component en appelant `FireEvent.click()`. <a href="https://twitter.com/afontq">Adria Fontcuberta</a> donnait également le conseil d'écrire des tests qui ressemblent le plus possible à ton application pour éviter les Faux positifs.

On a eu un talk de <a href="https://twitter.com/ipancreas">Jana Beck</a> sur la visualisation de données côté browser en utilisant Web Workers et Offscreen canvas. 

Quelqu'un (oui, je n'ai pas noté son nom -_-') a présenté le compilateur javascript <a href="https://stenciljs.com/">Stencil</a>. Le truc plutôt cool: il génère un graphe de dépendances, les bundles sont optimisés selon les liens entre les components, ce qui optimise les appels HTTP. 

<a href="https://twitter.com/IgorMinar">Igor Minar</a> a expliqué comment ils géraient les montées de version d'Angular. La mise en place de dépréciations en amont a aidé les utilisateurs à migrer plus facilement. Il conseille d'allouer un vrai budget pour les updates réguliers et d'automatiser les updates mineurs en utilisant des outils comme Dependabot. Il a montré un retour d'expérience de KLM qui prend de moins en moins de temps à migrer son application Angular (30jours sur les premières versions d'Angular contre 1 journée sur les versions récentes).

Il y a eu une présentation trop cool de qui a montré une application full serverless. Il a utilisé Evently (static site generator), FaunaDB en base de données et les fonctions Netlify, webtask.io : register crons online. Sa présentation est ici: https://findthat.at/servered

Sur la dernière présentation, Evan You a présenté un comparatif de la construction de components entre Svelte, Vue et React, faisant un parallèle entre les hooks (React) et Vue Composition API. 

C'est ce que j'ai retenu de cette première journée ! Plein d'enseignements, j'ai bien apprécié aussi le jour 2, dont le compte rendu arrive bientôt également :)