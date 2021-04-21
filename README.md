# nacos-sdk-php

A PHP implementation of Nacos OpenAPI.

see: https://nacos.io/zh-cn/docs/open-API.html

## Required

- PHP ^7.0

## Install

```bash
composer require Tinywan/nacos-sdk-php
```

## Getting Started

```php
use Nacos\NacosClient;

$client = new NacosClient('localhost', 8848);

$dataId = 'abc';
$group = 'test-group';
$value = $client->getConfig($dataId, $group);
```

## Docker

`http://127.0.0.1:8848/` replace `http://192.168.2.108:8848/` 
> ipconfig or ifconfig get `192.168.2.108`

## Other

```
psr4 Error: Class 'nacos\Client' not found
```
> need `composer dump-autoload`

## API

### Request Options

- setNamespace
  - string $namespace
- setTimeout
  - int $timeout

### Config API

- getConfig
  - string $dataId
  - string $group = NacosClient::DEFAULT_GROUP
- publishConfig
  - string $dataId
  - string $group
  - $content
- removeConfig
  - string $dataId
  - string $group = NacosClient::DEFAULT_GROUP
- listenConfig
  - array $configs
  - int $timeout = 30

### Naming API

- createInstance
  - ServiceInstance $instance
- deleteInstance
  - string $serviceName
  - string $ip
  - int $port
  - string $clusterName = null
  - string $namespaceId = null
- updateInstance
  - ServiceInstance $instance
- getInstanceList
  - string $serviceName
  - string $namespaceId = null
  - array $clusters = []
  - bool $healthyOnly = false
- getInstance
  - string $serviceName
  - string $ip
  - int $port
  - string $namespaceId = null
  - string $cluster = null
  - bool $healthyOnly = false
- sendInstanceBeat
  - string $serviceName
  - BeatInfo $beat

## Other

```
docker run --rm --interactive --tty -v e:/GitHub/nacos-sdk-php:/app composer:1.10.16 install --ignore-platform-reqs
```