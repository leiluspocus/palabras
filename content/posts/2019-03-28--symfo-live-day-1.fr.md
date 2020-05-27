---
title: Symfony Live - Jour 1
date: "2019-03-28T19:23:42+00:00"
description: Débrief de la conférence Symfony Live à Paris en mars 2019
template: post
draft: false
slug: /fr/symfony-life-mars-2019-jour-1
category: Conférences
tags:
  - conferences
  - symfony
  - php
---

# Récapitulatif - SymfonyLive 2019 Jour 1

Mais qu'est-ce que je retrouve ? Des notes que j'avais prises en mars 2019 lors de la Symfony Live à Paris ! 

NDLR: Elles sont un peu en vrac.

# Keynote 
Symfony Mime > Swift_Mailer 
+ Moins d’objets à serializer 
+ Headers pas determines a l’avance 
+ intégration native avec twig, embarque l’objet email : méthode template / textTemplate / htmlTemplate à utiliser. 
+ Inky pour simplifier templating 
+ séparation envoi et création 
+ Symfony mailer juste pour mails transactionnels 
>> http : body déjà construit, api: il le construit par le provider 

Security.symfony.com : On peut y uploader composer.lock pour checker les failles de sécurité 


# Symfo / React 

insights.symfony.com 
- Mutations induites par changement sur l’UI. 
- Mutations complexes à reproduire appliquer DEBUG. 
- Dispatcher > Store > view 
React rerenders view when data changes >> slow. 
- La fonction render fabrique un arbre de composants correspondant à la représentation de la vue. 

Webpack encore 



# Symfo / Vue.js (Les Tilleuls Coop)

Approche Rich client ==> API driven. 
joind.in => noter conférences. 
symfonycon.les-tilleuls.coop 

> bin/console make:entity pour générer des entités CLI

Côté server: hypermedia API / Client-side: web components JS. 
Recette dispo sous Symfo 4 pour API Platform. Code dispo sur Github. 

BrowserKit > simuler des scénarios de navigation sur browser (PHP)

Symfony Panther => test end to end. Quelques méthodes intéressantes > attendre qu’un élément apparaisse sur la page. Rien à configurer officiellement. 

Fixtures 
> composer req alice. 
Implémenter ReloadDatabaseTrait >> Reload les fixtures avant chaque test. Plus besoin du script pour lancer les fixtures. (Panther vs Behat ?). 
Fait des screenshots aussi. 

mercure.rocks > Hub maintient les connexions persistantes. (intéressant pour les notifs)

Annotation Mercure true sur API Platform pour broadcaster derrière une info au hub.
 

# Elasticsearch + Symfo

Pas de données critiques sur Elasticsearch. 
Noeud : Instance d’ElasticSearch qui tourne. Création d’index dans le cluster. 
Elastica => Bibliothèque recommandée pour manipuler ElasticSearch. 

noyaml.com yawl anchor 
dynamic false pour ne pas laisser elasticsearch deviner le type de la donnée à indexer

Indexer le minimum de données, juste le nécessaire à la recherche.

## Accélérer indexation

Côté PHP: 
- Faire des traitements par bulk
- Black fire pour tracer
- Utiliser un serializer rapide (Jane?)
- Doctrine iterate. 

Côté elasticsearch: 
- refresh_interval à augmenter + désactiver les replicas. 
- optimiser le temps passé sur le réseau côté infra (node es qui communique avec frontal php, node communique avec es clusters)

## Pertinence des résultats :
- ?explain=true pour avoir une explication du score de la recherche donné par elasticsearch. 

## SQL avec ElasticSearch: 
POST /_sql
{query: "select * from table" }

Kibana = PHPStorm d'ES.



# HTTP/3 @bjacquemont 

HTTP/2 = 2015 
HTTP/2 = 2018

TCP 
Client -> Syn 
Serv -> Syn Ack
Client -> Ack
Client -> Requête

TCP Handshake => Latency. 

Latence : on se heurte à des limites physiques (vitesse de la lumière). 
3 important time limits in UX :
- 0.1s: instantaneous feeling limit
- 1s flow of thought limit
- 10s user attention limit

> ennemi of UX. 

HTTP2: Multiplexer les requêtes au sein d’une connexion HTTP

TCP + TLS (8 étapes) + TLS => 90% du temps de latence est passé dans l’établissement de la connexion. 
TCP ne connaît pas TLS. TCP établit connexion mais n’est pas au courant de sa sécurisation. 
QUIC : Protocole de transport remplaçant TCP basé sur UDP. 
Qui Handshake 
Initiator : Quickness’s hello -> Quickness’s token -> quickness’s hello + token: en trois étapes, on génère une connexion fiabilité et chiffrée avec moins de latence que TCP / TLS. 

Quic va devoir implémenter les fonctions manquantes perte de paquets réémission + réordonnancement de paquets : navigateur / serveur 

Couplage fort entre TCP et réseau internet : si un casse, l’autre se casse aussi. (déconnexion quand on change de réseau). 

Réduction de la latence, migration de réseau possible sur QUIC (couplage faible).
HTTP2 : Possibilité de faire plusieurs requêtes en parallèle. Connectivité mauvaise (métro) :  streams can fail easily. 
QUIC a conscience des streams HTTP. Possibilité d’utiliser les données qui sont arrivées en attendant le reste. 
Streams QUIC sont indépendants les uns des autres même si on est dans la même connexion QUIC. 

HTTP3 = HTTP2 basé sur QUIC. Sémantics ne changent pas. HTTP/3 is a drop in replacement for HTTP/2 : préparations pour HTTP/2 seront valides. 

Firewall configuration: Firewall usually opened only for TCP for 80 and 443. 

Maturité de QUIC : Lancé en 2013 par Google, enbled sur Chromium. Standardisation en cours via l’IETF. Sortie officielle cette année ou 2020. 

Cloudflare support QUIC. Varnish: WIP. Pas de module Nginx / Apache.  

daniel.haxx.se/blog/tag/auic 


# Images sous Symfo

DPR : Device Pixel Ratio. mydevice.io pour voir les dimensions physiques + leur device pixel ratio. 
width et height dans balise img pour réserver l’espace dans le layout.

Navigateur selon la qualité du réseau va  pouvoir changer sa source d’images. 

Chargement des pages:
- Navigateur charge le DOM
- Le parse
- Lance les requêtes pour loader les assets externes.

Au parsing du DOM, le navigateur connait le DRP de l’appareil, les dimensions du viewport et la qualité du réseau. 

https://responsivebreakpoints.com génère breakpoints d’images. 

github.com/clavetage/daltons : Utilitaire CLI pour générer des breakpoints d’image à partir de données analytics

attribut srcset + sizes pour indiquer au navigateur la largeur de la balise img. 
L’ordre des sources dans secret n’a pas d’importance. L’ordre des medias queries dans l’attribut sizes a une importance (premier saisi premier interprété). Le premier attribut media utilisé est vérifié. 

Glide + LiipImagineBundle (gère pas la sécurité) - Symfony pour la génération d’images. 




# Du développement à la prod : une architecture grandissante 

Accès au site = File d’attente 
Vitesse de chargement des pages = Traitement du service 

Optimisation des requêtes / processus PHP / nb dépendances / poids images js html css / optimisation des redirections ==> Effet Papillon 

DevOps Lifecycle Mesh. 

Fastly = version CDN de Varnish. 
Ajout de layers : serveurs de cache HTTP (Varnish), cache de persistence de données (Redis Memcached). 

etag : hash correspondant à la ressource, être sûr de son unicité. 

Varnish : Fichier de configuration (vcl) ou on peut rajouter du C.Requête HTTP arrive sur le vcl_receive (vcl_recv). 
varnish stat pour monitorer ( CACHE HIT : Nombre d’objets en cache dans la mémoire Varnish doit être supérieure au CACHE MISS). 
Varnish Log  : varnishlog -g request -q « RespStatus >= 500 »


Cache de persistence - Redis
- Mécanisme de réplication simple ( master / slave pour backup ) 
- Réplication avec Sentinels (Service à installer en même temps que Redis. Ces Sentinels vont dialoguer ensemble pour élire un nouveau master en cas de fail)
- Redis Cluster (réplication fournie par Redis directement)

Galera Cluster 
Système de réplication BDD. 
Règles: Plus de 50% de noeuds pour maintenir les opérations. Galera a besoin de 3 serveurs minimum pour fonctionner. Chaque noeud doit valider la requête pour qu’elle soit exécutée. 

## Bundles intéressant pour le cache: 

Fos HTTP Cache Bundle. 
UserContext : Faire varier le bloc de cache selon l’user. Droits utilisateur sous forme de chaîne de caractère : tous les users ayant les mêmes droits voient les mêmes données cachées. Cache désactivable sur une page dans le YAML.
Symfony Cache Component (PSR6 PSR16) 

 

# Bundles et outils pour applis Symfo

PHP CS Fixer 
FriendsOfPHP/PHP-CS-Fixer  > correction automatique
phpmd/phpmd
phpstan/phpstan 

Hooks locaux / Hooks distants 

GrumPHP > tasks : on active les outils de qualité dont on a besoin. 

fabbot.io > validation service for GitHub pull requests 

Outils de qualité 
Symfony Insights
alice-bundle == doctrine-fixtures-bundle 


Documentation d’une API REST : BelmioApiDocBundle documentation au format OpenAPI. 
guzzle/guzzle : consommer des web services facilement. Couche d’abstraction pour les requêtes Http. 
Http Client: symfony/http-client : experimental feature 

Sécuriser API : 
- Json Web Token lexie : authentification par jeton JWT. 
- OAuth hwi/HWIOAuthBundle. 

DoctrineExtension : Via des annotations, faire du tri, softdelete. 

FOSEslasticaBundle (ElasticSearch)
algolia/search-bundle 
Glide : HTTP based image manipulation. 

Composant Messenger à la place de AMQP ?

Monolog => Possibilité d’envoyer des alertes sur Slack. Envoi aux serveurs spécifiques. Affichage dans les consoles navigateur. 

Sentry -> Real time crash reporting sentry/sentry-symfony : la payload est renseignée / navigateur du user. 

Critères de sélection: packagist (nombre de downloads, contributeurs, stars, date du dernier commit). 

Single Responsibility
Open Closed 
Liskov Substitution
Interface Segregation 
Dependency Inversion 

Packages Principles 
Les classes sont nécessaires mais insuffisantes pour organiser un système. Utiliser les packages. 

Package principes
Principe de cohésion (granularité) + principe de couplage (stabilité / dépendance). 


Abstract Syntax Tree : Analyseurs de code utilisent cette représentation pour détecter les erreurs. 

SymfonyChecker => façon d’analyser dynamiquement le code pour supprimer les traductions inutilisées, tout est local. 

symfony => binaire en Go installable en local 