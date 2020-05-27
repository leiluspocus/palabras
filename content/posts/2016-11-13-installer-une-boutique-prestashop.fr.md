---
title: Installer une boutique Prestashop
date: "2016-11-13T11:19:27+00:00"
description: "J'ai installé une boutique Prestashop from scratch dans le cadre d'un projet. Voici un petit débrief de mon expérience."
template: post
slug: /fr/installer-une-boutique-prestashop/
category: Snippets
tags:
  - devops
  - prestashop
---


# Gestion d&rsquo;environnements

_Références vers la racine de la boutique_

  - **.htaccess** à la racine du projet
  - Tables **ps_configuration** et **ps\_shop\_url**.

_Références vers la base de données_

  - Fichier app/config/parameters.php

```php 
<?php return array (
  'parameters' => 
  array (
    'database_host' => 'host',
    'database_port' => '',
    'database_name' => 'db_name',
    'database_user' => 'db_user',
    'database_password' => 'db_pwd',
    'database_prefix' => 'tbl_prefix',
    'database_engine' => 'InnoDB',
    'mailer_transport' => 'smtp',
    'mailer_host' => '127.0.0.1',
    'mailer_user' => NULL,
    'mailer_password' => NULL,
    'secret' => '75En87VA6bfCemg6GZF7eAFJd2jdK6yFDZ9kGE0BFXuHdAyzID1z7W7d',
    'ps_caching' => 'CacheMemcache',
    'ps_cache_enable' => false,
    'ps_creation_date' => '2016-11-01',
    'locale' => 'en-US',
    'cookie_key' => '',
    'cookie_iv' => '',
    'new_cookie_key' => 'def00000b022f8a238accf3dbce07c8637935009e0a5ea637e8d1611e06d0ce97edf93af5cf40871d560287eef4990de0801a01df04fbb002184c3e8804d73939d2720e8',
  ),
);
```

&nbsp;

# Activation du mode debug

```php 
// Dans le fichier config/defines.inc.php
if (!defined('_PS_MODE_DEV_')) {
define('_PS_MODE_DEV_', true);
}
```
