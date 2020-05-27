---
title: Github pour les nuls
date: "2013-02-10T23:14:59+00:00"
template: post
slug: /fr/github-pour-les-nuls/
category: Cheatsheet
draft: false
tags:
  - cheat sheet
  - git
  - github
---
Nous sommes souvent amenés à l&rsquo;UTC à travailler sur de petits projets en groupe. Pour avoir effectué du développement en groupe sans gestion de versonning, le travail devient vite compliqué au moment où l&rsquo;on réunit les sources. GitHub serait une solution puisqu&rsquo;il s&rsquo;agit d&rsquo;un service hébergeant à distance les dépôts centralisés (sur lesquels peuvent travailler plusieurs ressources).

  * <a href="http://www.sans-savoir.net/2008/05/07/github-vos-depots-distants-pour-git/" target="_blank">Présentation de Git / GitHub</a>
  * <a href="http://www.grafikart.fr/tutoriels/internet/git-github-131" target="_blank">Tutoriel vidéo</a>
  * <a href="http://www.siteduzero.com/tutoriel-3-254198-gerez-vos-codes-source-avec-git.html#onglets_tutos" target="_blank">Commandes Git</a>

Quelques tips pour se brancher à un repo déjà existant :

  1. Cliquer sur « Fork » sur la page du repo
  2. Lancer la commande « git clone git@github.com:_<votre login>_/<nom de votre repo>.git »
  3. Dans le dossier du repo, lancer la commande « git remote add _upstream_ git@github.com:<login du createur du repo>/<nom du repo>.git »

<div>
  <em>upstream</em> désigne l&rsquo;alias de connexion au repo distant, vous auriez pû aussi l&rsquo;appeler tata, l&rsquo;essentiel est de se retrouver dans les différents noms. A noter qu&rsquo;il existe un alias par défaut appelé « origin » qui pointe vers le repo local, crée au moment du fork ! (c&rsquo;est sur ce repo que se dirigeront vos futurs commits).
</div>

A noter que ces commandes peuvent être exécutées s&rsquo;il s&rsquo;agit d&rsquo;un repository **privé** ! Ensuite pour effectuer ses commits, il suffit d&rsquo;exécuter les commandes « git commit -a » (pour commiter tous les fichiers modifiés), puis « git push upstream master » pour les envoyer sur le repo de référence.

