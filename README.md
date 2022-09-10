# PSR logger meets Doctrine

Log doctrine logs any where with PSR loggers.

## Table of contents

- [Install](#install)
- [Usage](#usage)

## Install

Via Composer

``` bash
$ composer require benycode/doctrine-psr-logger
```

## Usage

Then you are setting up Doctrine EntityManager setup logger (in example i'm using DI):

```php
EntityManager::class => static function (ContainerInterface $container): EntityManager {
  ...
		
  $logger = .....
    ->addFileHandler('database.log')
    ->createLogger()
  ;
		
  $config
    ->setSQLLogger(new \BenyCode\DoctrinePsrLogger\PsrSqlLogger($logger))
  ;
  
  return EntityManager::create($settings['db'], $config);
},
```
