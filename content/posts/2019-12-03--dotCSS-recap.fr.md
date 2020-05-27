---
title: Un après-midi à dotCSS
date: "2019-12-07T19:23:42+00:00"
description: Débrief de la conférence dotCSS à Paris en décembre 2019
template: post
draft: false
slug: /fr/recapitulatif-dotCSS-decembre-2019
category: Conférences
tags:
  - conferences
  - css
---

# Récapitulatif - dotCSS 2019 

J'ai eu la chance d'assister à dotCSS cette année grâce à des places qui ont été offertes par les dotConferences à la communauté <a href="https://paris.ladiesofcode.com/" target="_blank">Ladies of Code</a>. 

La conférence a commencé très fort avec une conférence de Sarah Dayan, ingénieure chez Algolia. Elle y a introduit le concept d'utility-first CSS CSS est plus efficace lorsqu'on utilise comme une bibliothèque en raison des dépendances entre le HTML et le CSS. Un composant ne sera pas réutilisable dans sa globalité, autant factoriser de plus petits éléments (typographie similaire, ou icône).
Le CSS est plus petit à parser par le navigateur puisqu'à un seul niveau de profondeur, plus rapide à resolve. 
Elle y fait une démonstration <a href="https://github.com/sarahdayan/utility-first-compression-demo/blob/master/README.md">d'un outil qu'elle a crée pour la factorisation des classes redondantes</a> entre éléments du DOM grâce à Brotli (algorithme de compression). Le benchmark de performance est impressionnant. 
Sa présentation est accessible <a href="https://noti.st/sarahdayan/pmD0XT/in-defense-of-utility-first-css">ici</a>. 

S'en est suivi des présentations autour de l'accessibilité et l'importance de réfléchir avant de défaire un comportement natif du navigateur. 
```
:focus {
    outline: none;
}

div {
    display: contents; // pouvoir être lu par le VoiceOver
}
```

Ces propriétés peuvent être utiles dans un contexte d'accessibilité où l'utilisateur est contraint d'utiliser un clavier pour sa navigation ou un système de voice-over. Il est possible de créer des règles spécifiques pour les utilisateurs qui ne peuvent pas voir d'animations pour des raisons d'handicap: prefered-reduced-motion à ajouter dans une media query séparée. 

``` 
Transition: all 600ms // not working on Chrome.
```

J'y ai appris l'existence du site http://www.testmycss.com/ pour l'analyse et l'optimisation d'un fichier CSS. 

Jérémie Patonnier nous a raconté <a href="https://jeremiepat.github.io/svg-css-bff/">la belle histoire d'amitié entre SVG et CSS</a> et m'a donné envie de jouer un peu plus avec ces deux là :) 

<a href="https://twitter.com/emplums">@emplums</a> a présenté <a href="https://primer.style/components/">PrimerComponents</a>, une bibliothèque de components React qui implémentent le design system de Github. 

Durant un lightning talk (je n'ai pas noté le nom de la personne malheuresuement), j'ai appris qu'il était possible de runner du JS dans du CSS ! 😱 (je prendrai un peu de temps pour fouiller sur Twitter et updater cet article avec son incroyable codepen!)

Jason Pamental a parlé <a href="https://noti.st/jpamental/Z0MwNQ/dynamic-typographic-systems-with-variable-fonts">typographie</a> et a présenté le concept des custom properties et variables fonts. J'ai aussi découvert dans ce talk qu'il était possible de target le dark-mode en CSS encore via... une media query ! (Moi qui pensais bêtement qu'on ne pouvait mettre que des tailles de device dans ces petites choses !). Ses slides sont <a href="https://noti.st/jpamental/Z0MwNQ/dynamic-typographic-systems-with-variable-fonts">par ici</a>.

Pour finir, Ires nous a plongé dans l'état actuel et futur de CSS (spoiler alert: on est déjà dans le futur!). J'y ai découvert Houdini, un set d'API qui exposent une partie de l'engine CSS. Je creuserai définitivement <a href="https://developer.mozilla.org/en-US/docs/Web/Houdini">la doc MDN à ce sujet</a>. 

Elle nous a expliqué le concept des <a href="https://hacks.mozilla.org/2016/08/using-feature-queries-in-css/">Features Queries en CSS</a> sous-utilisées à son goût, qu'il vaut mieux utiliser positivement que négativement (et mettre le fallback dans le body par défaut). Elle nous a rappelé de tirer profit du rôle "cascade" de CSS, de tirer profit des préférences utilisateur pour une meilleure accessibilité (color scheme // animations // adapt data consumption preferences).

Elle nous a aussi parlé d'un futur où il faudra considérer plus de pays et des problématiques d'inclusivité plus diverses pour le web: les concepts d'internationalisation seront à prendre en compte. Un ```margin-left``` n'aura pas le même sens pour un européen habitué à lire de gauche à droite et de haut en bas que pour une personne asiatique ou arabe. Les problématiques de données seront aussi. Je vous recommande vraiment de revoir son talk qui était très agréable à écouter. 

C'est tout pour moi ! C'était top, j'y retournerai définitvement l'an prochain si j'en ai l'opportunité :) 