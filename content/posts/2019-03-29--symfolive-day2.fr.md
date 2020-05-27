---
title: Symfony Live - Jour 2
date: "2019-03-29T19:23:42+00:00"
description: Débrief de la conférence Symfony Live à Paris en mars 2019
template: post
draft: false
slug: /fr/symfony-life-mars-2019-jour-2
category: Conférences
tags:
  - conferences
  - symfony
  - php
---

# Récapitulatif - SymfonyLive 2019 Jour 2

Mais qu'est-ce que je retrouve ? Des notes que j'avais prises en mars 2019 lors de la Symfony Live à Paris ! 

NDLR: Elles sont un peu en vrac.

# Talk #1: Open Source - Renouveau de l'humanisme
- Principe anthropique = Tout est orienté pour faire apparaître la vie organique. 
- Interdépendance entre chaque membre d'une communauté = ubuntu
- "Ubuntu" = I am because we are. 
- Symfony Diversity Initiative
- Communauté Drupal => Clash lié à la diversité. 
- L'inclusivité ne s'arrête pas à l'égalité F-H.

# Talk #2 : Passion Doctrine 

Derrière le Query Builder, Doctrine prépare un statement. 

Doctrine construit un objet a partir de la BDD: hydratation. Changer l'hydratation pour les performances. L'hydratation en object surtout avec des objets associés est très lourde. 

## Changer le mode d'hydrataion
HYDRATE_SIMPLEOBJECT => warning avec getters.

## Partial object. 
Il faut se souvenir des champs que l'on récupère pour 
éviter des NPE.

## Partial references 
Récupérer une entité que pour son ID: ```$entityManager->getPartialReference```

orphanRemoval => Un article est associé à un blog et ne peut exister sans blog. 

Dans la mesure du possible, Doctrine propose du lazy loading : proxy ou une PersistentCollection à la place des entités jointes.

- Les proxies supportent mal la sérialisation. 
- Utiliser les criteria dans le getter de l'entité.
- Utiliser les filtres

## Organiser ses repositories 
- Factoriser les clauses where appelées régulièrement. 
- Ou faire un builder de QueryBuilder

## Lifecycle callbacks 

- Implémenter les Entity Listener 
- On a pas besoin de persist() par défaut. Possibilité de changer ça via la trackingPolicy

## Optimiser la trackingPolicy pour les perfs 
- Deferred Explicit (utilise moins de ressources mais attention aux cascades)
    - Les annotations ne suffisent pas. 
- Notify : le plus optimisé mais lourd à mettre en place 
- On ne peut pas faire de flush depuis un listener Doctrine

## Mappings

### Embeddable
Annotation \Embeddable pour embarquer directement une classe dans une entité. DQL on peut directement faire un join dans la classe 
MappedSuperclass : déconseillé. Si pas d'héritage, utiliser les Traits. 

### Caches 
- **metadata_cache_driver (cache annotations) + query_cache_driver (cache DQL) à activer en prod ** !
- result_cache_driver: apcu (optionnel et manuel) 
- second=level cache 

steevanb/DoctrineStatsBundle => bundle sympa pour débugguer + optimiser les performances de page. 

Slides à venir sur le twitter de @romaricdrigon Présentation hyper complète, on adore. 

# Talk #3 : API Platform 

Twitter @gheb_dev 

- Annotation @APIResource : CRUD complet disponible + doc swagger. 
- mercure=true / messenger=true option dans l'annotation APIResource 
  - plutôt que de l'envoyer en BDD, APIPlatform va intercepter la ressource et l'envoyer sur AMQP ou al. 


# Talk #4 : Symfony HTTP Client
@nicolasgrekas
Package standalone. Implémente PSR-18. Utilisable même sur des projets hors Symfo. 

- Faire des requêtes facilement
- Remplace GuzzleHttp\Client

Découplage du composant. Il consomme une abstraction (HTTPClientInterface).
Stateless (autowired) service. 

Bearer / JSON payload peut être passé dans les options de la requête (3ème arg). 

Form parameters (form_params sur guzzle) peut directement être passé dans le body de la requête. 

## Options de $client->request 
- proxy - get through an http proxy
- on_progress - afficher une progress bar / interrompre une requête 
- base_uri - construire une URL absolue
- resolve - bypasser résolution DNS : empêcher d'appeler des endpoints internes
- max_redirects - désactiver ou limiter les redirections 

FailSafe par défaut : si on recoit un statut code 3/4/5xx ça jette une exception (désactivable mais pas cool)

Streameable downloads sur une réponse. 

Les Responses sont lazy et les requêtes sont concurrentes. 
```$response->getStatusCode()``` 
On attend pas que la totalité de la réponse arrive pour retourner la réponse. On attend juste les headers. 

Sur les chunks, il existe une méthode ```isLast``` pour détecter que c'est le dernier du stream.

```$response->getInfo('user_data')``` 
- Avoir des infos sur ce qui s'est passé au niveau de la réponse. 
- Recopie une valeur passée au moment de la request.

379 requêtes en 0,4s (utilise curl sous HTTP2) sur l'ex de la demo. 

Fait pour HTTP/2 PUSH. 


## Component consommateur 
NativeHttpClient utilise fopen, CurlHttpClient basé sur curl. 

- Beaucoup d'infos sur les temps passés dans la requête

NativeHttpClient est la plus portable. Bloquant jusqu'à ce que les réponses de header arrivent. 

CurlHttpClient utilise ext-curl. Gère le multiplexing au niveau des entêtes et du body. 0 latence. La quasi totalité des options curl sont couvertes par l'abstraction à la différence de Guzzle où on peut forcer les options #notclean

## Décorateurs 
- MockHttpClient - Pour les tests, ne fait pas de requête
- CachingHttpClient - Headers Cache Controls gérés
(cf: slides)


# Talk #5: React-admin - Admin Generator d'API Platform 
@francoisz
marmelab/react-admin 

Conseils pratiques: Comment se mettre au développement front quand on est dev Symfo ? 

```<HydraAdmin entrypoint="api"></HydraAdmin>```
- Ejecter l'AdminBuilder et utiliser le composant natif de react-admin : Admin
    - Avoir la main sur son admin. 
- Éviter les entités embeddées 

Annotation @Group pour préciser les colonnes qu'on veut récupérer côté admin.

Onglet Redux sur Chrome ! (Comme Vue)

react-admin communique avec l'API au travers du data provider. 

Évaluer la variable d'environnement dans l'objet window : 
```javascript
window.config = {
    edit: false
};
// Immutable Web Apps
```

Récupérer aussi les slides, y avait une alternative intéressante UI pour ouvrir un panel. 

# Talk #6: Rabbit MQ

Déclarer les messages persistants si on veut qu'ils restent dans la queue au redémarrage. 

Par défaut, rabbitMQ cnsomme trois messages. 
Reject / NACK : Possibilité complémentaire: rejeter les  messages dans prefecth, tout repart dans la queue. Oublier reject. 

On publie un message dans un exchange (point de diffusion d'un message). La queue se binde dans l'exchange. Sans queue, pas de message. 

On publie le message avec une routing key unique. Chaque queue peut s'abonner à différences keys. 
- "topic" permet d'avoir des wildcards dans les binding keys auquelles s'abonner. 
- "direct" routing key doit être identique à la binding key. 
- "headers" message porte l'information de routing 
- "fanout" on distribue tout à n'importe qui. 

Dead Letter Exchange : Récupérer les messages en erreur et les envoyer sur un exchange sur lequel une queue pourra être bindée. 
Un TTL peut être défini pour envoyer le message en DLX. 

conposer require messenger 

NotifyMessageHandler qui implèmente MessageHandlerInterface. Prend un MessageBusInterface et peut envoyer un message à Rabbit. 

composer require amqp-pack : possibilité de configurer un transport avec son DSN.  

# Talk #7 : TDD Symfo et ses amis

Slides accessibles ici: https://bit.ly/real-world-tdd

Cycle : 
- Failing Test
- Make test pass
- Refactor 

Codeception ? 
- DTOs = Data Transfer Objects

## Test-Driven Repositories 
- Unit Test: ORM branché sur une base de donnée en mémoire (ex: SQLite) 
- Manuellement: Branché sur MySQL

migration:diff -> compare les schémas et crée les migrations nécessaires pour mettre le schéma de la BDD à jour. 

https://bit.ly/tdd-vids 

Brancher Doctrine : 
- config_test.yml <-- Utilisé par PHPUnit 
```yaml
doctrine:
  dbal:
      driver: pdo_sqlite 
```