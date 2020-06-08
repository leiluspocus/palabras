---
title: Atomic Design
date: "2014-02-10T23:30:36+00:00"
template: post
draft: false
slug: /fr/atomic-design/
category: Design
tags:
  - atomic design
  - principes
  - ux design
---


> 👴 _Attention_ Cet article a quelques années et n'est peut-être plus à jour !

J&rsquo;ai trouvé cet excellent [article](http://bradfrostweb.com/blog/post/atomic-web-design/) écrit par [Brad Fost](https://twitter.com/brad_frost) qui explique les concepts de l&rsquo;atomic web design, en voici un petit résumé.

L&rsquo;Atomic Design est une méthodologie de conception de systèmes. L&rsquo;idée est que chaque système est décomposable en plusieurs niveaux pouvant être imbriqués les uns avec les autres. On commencera la conception d&rsquo;un design par le plus petit niveau.

  1. Niveau « Atome »
  
  Il s&rsquo;agit de l&rsquo;élément le plus basique d&rsquo;une page HTML. Ce peut être par exemple un bouton ou un label.

  2. Niveau « Molécule »
  
  Il s&rsquo;agit d&rsquo;un regroupement d&rsquo;atomes: l&rsquo;exemple donné dans l&rsquo;article est un fieldset de recherche (input pour la zone de texte avec un label et un bouton). Il s&rsquo;agit de la plus petite unité fonctionnelle d&rsquo;un site Internet.

  3. Niveau « Organisme »
  
  Il s&rsquo;agit d&rsquo;un regroupement de molécules: autrement dit, on regroupe plusieurs fonctionnalités ensemble pour former une section de l&rsquo;interface finale. Ce peut être par exemple l&rsquo;en-tête d&rsquo;une page.

  4. Niveau « Template »
  
  Le design du site Internet commence à prendre forme à ce niveau. Ce niveau regroupe plusieurs organismes et donnent ainsi un contexte en regroupant ces éléments, qui sont abstraits lorsqu&rsquo;ils sont considérés séparement.

  5. Niveau « Page »
  
  Cela représente le rendu final donné au client. Instance spécifique d&rsquo;un template, il contiendra le contenu , les images propre à un certain projet.

_Quel est l&rsquo;intérêt ?_

L&rsquo;intérêt de cette approche méthodologique est de contrôler plus efficacement la conception d&rsquo;un design en développant des éléments ré-utilisables. La création de molécules favorise la ré-utilisation d&rsquo;éléments dans différents designs.

_Sources_

http://coding.smashingmagazine.com/2013/08/02/other-interface-atomic-design-sass/

<!-- AddThis Advanced Settings generic via filter on the_content -->

<!-- AddThis Share Buttons generic via filter on the_content -->