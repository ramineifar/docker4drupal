# Docker-based Drupal stack

[![Build Status](https://github.com/wodby/docker4drupal/workflows/Run%20tests/badge.svg)](https://github.com/wodby/docker4drupal/actions)

## Introduction

This version of Drupal initialization development platform is base on Docker4Drupal [latest stable release](https://github.com/wodby/docker4drupal/releases) to spin up local environment on Linux, Mac OS X and Windows. 

## Stack

The Drupal stack consist of the following containers:

| Container       | Versions               | Image                              | ARM64 support | Enabled by default |
| --------------- | ---------------------- | ---------------------------------- | ------------- | ------------------ |
| [Nginx]         | 1.20, 1.19             | [wodby/nginx]                      | ✓             | ✓                  |
| [Apache]        | 2.4                    | [wodby/apache]                     | ✓             |                    |
| [Drupal]        | 9, 8, 7                | [wodby/drupal]                     | ✓             | ✓                  |
| [PHP]           | 8.0, 7.4, 7.3          | [wodby/drupal-php]                 | ✓             |                    |
| Crond           |                        | [wodby/drupal-php]                 | ✓             | ✓                  |
| [MariaDB]       | 10.5, 10.4, 10.3, 10.2 | [wodby/mariadb]                    | ✓             | ✓                  |
| [PostgreSQL]    | 13, 12, 11, 10, 9.6    | [wodby/postgres]                   | ✓             |                    |
| [Redis]         | 6, 5                   | [wodby/redis]                      | ✓             |                    |
| [Memcached]     | 1                      | [wodby/memcached]                  |               |                    |
| [Varnish]       | 6.0, 4.1               | [wodby/varnish]                    |               |                    |
| [Node.js]       | 14, 12, 10             | [wodby/node]                       |               |                    |
| [Drupal node]   | 1.0                    | [wodby/drupal-node]                |               |                    |
| [Solr]          | 8, 7, 6, 5             | [wodby/solr]                       |               |                    |
| [Elasticsearch] | 7, 6                   | [wodby/elasticsearch]              |               |                    |
| [Kibana]        | 7, 6                   | [wodby/kibana]                     |               |                    |
| [OpenSMTPD]     | 6.0                    | [wodby/opensmtpd]                  |               |                    |
| [Mailhog]       | latest                 | [mailhog/mailhog]                  |               | ✓                  |
| [AthenaPDF]     | 2.16.0                 | [arachnysdocker/athenapdf-service] |               |                    |
| [Rsyslog]       | latest                 | [wodby/rsyslog]                    |               |                    |
| [Blackfire]     | latest                 | [blackfire/blackfire]              |               |                    |
| [Webgrind]      | 1                      | [wodby/webgrind]                   |               |                    |
| [Xhprof viewer] | latest                 | [wodby/xhprof]                     |               |                    |
| Adminer         | 4.6                    | [wodby/adminer]                    |               |                    |
| phpMyAdmin      | latest                 | [phpmyadmin/phpmyadmin]            |               |                    |
| Selenium chrome | 3.141                  | [selenium/standalone-chrome]       |               |                    |
| Traefik         | latest                 | [_/traefik]                        | ✓             | ✓                  |
 
Supported Drupal versions: 9 / 8 / 7

## Documentation

This code version is based on the last edition of [wodby documentation](https://wodby.com/docs/stacks/drupal/local) using our code coverage.

This version integrates some code to download automatically Drupal Core and inject database credentials.

* create .env file from .env.dist file and inject the database credentials want to use.
* you can change default information of project
  * `PROJECT_NAME=your-project-name` *The project name used to create container*
  * `PROJECT_BASE_URL=your-host-name.com` *Host name of project*
  * `PROJECT_NAME_PORT=80` *Port associate to host name to access site*
  * `PROJECT_ADMIN_NAME=admin` *name superuserdrupal uid 1* 
  * `PROJECT_ADMIN_PASS=admin` *password superuser drupal uid 1*
* execute `make install` to build container and download Drupal Core

> To choose Drupal Core version override informations on web/composer.json before `make install`

## Images' tags

Images tags format is `[VERSION]-[STABILITY_TAG]` where:

`[VERSION]` is the _version of an application_ (without patch version) running in a container, e.g. `wodby/nginx:1.15-x.x.x` where Nginx version is `1.15` and `x.x.x` is a stability tag. For some images we include both major and minor version like PHP `7.2`, for others we include only major like Redis `5`. 

`[STABILITY_TAG]` is the _version of an image_ that corresponds to a git tag of the image repository, e.g. `wodby/mariadb:10.2-3.3.8` has MariaDB `10.2` and stability tag [`3.3.8`](https://github.com/wodby/mariadb/releases/tag/3.3.8). New stability tags include patch updates for applications and image's fixes/improvements (new env vars, orchestration actions fixes, etc). Stability tag changes described in the corresponding a git tag description. Stability tags follow [semantic versioning](https://semver.org/).

We highly encourage to use images only with stability tags.

## Maintenance

We regularly update images used in this stack and release them together, see [releases page](https://github.com/wodby/docker4drupal/releases) for full changelog and update instructions. Most of routine updates for images and this project performed by [the bot](https://github.com/wodbot) via scripts located at [wodby/images](https://github.com/wodby/images).

## Beyond local environment

Docker4Drupal is a project designed to help you spin up local environment with docker-compose. If you want to deploy a consistent stack with orchestrations to your own server, check out [Drupal stack](https://wodby.com/stacks/drupal) on Wodby ![](https://www.google.com/s2/favicons?domain=wodby.com).

## License

This project is licensed under the MIT open source license.

[Apache]: https://wodby.com/docs/stacks/drupal/containers#apache
[AthenaPDF]: https://wodby.com/docs/stacks/drupal/containers#athenapdf
[Blackfire]: https://wodby.com/docs/stacks/drupal/containers#blackfire
[Drupal node]: https://wodby.com/docs/stacks/drupal/containers#drupal-nodejs
[Drupal]: https://wodby.com/docs/stacks/drupal/containers#php
[Elasticsearch]: https://wodby.com/docs/stacks/elasticsearch
[Kibana]: https://wodby.com/docs/stacks/elasticsearch
[Mailhog]: https://wodby.com/docs/stacks/drupal/containers#mailhog
[MariaDB]: https://wodby.com/docs/stacks/drupal/containers#mariadb
[Memcached]: https://wodby.com/docs/stacks/drupal/containers#memcached
[Nginx]: https://wodby.com/docs/stacks/drupal/containers#nginx
[Node.js]: https://wodby.com/docs/stacks/drupal/containers#nodejs
[OpenSMTPD]: https://wodby.com/docs/stacks/drupal/containers#opensmtpd
[PHP]: https://wodby.com/docs/stacks/drupal/containers#php
[PostgreSQL]: https://wodby.com/docs/stacks/drupal/containers#postgresql
[Redis]: https://wodby.com/docs/stacks/drupal/containers#redis
[Rsyslog]: https://wodby.com/docs/stacks/drupal/containers#rsyslog
[Solr]: https://wodby.com/docs/stacks/drupal/containers#solr
[Varnish]: https://wodby.com/docs/stacks/drupal/containers#varnish
[Webgrind]: https://wodby.com/docs/stacks/drupal/containers#webgrind
[XHProf viewer]: https://wodby.com/docs/stacks/php/containers#xhprof-viewer

[_/traefik]: https://hub.docker.com/_/traefik
[arachnysdocker/athenapdf-service]: https://hub.docker.com/r/arachnysdocker/athenapdf-service
[blackfire/blackfire]: https://hub.docker.com/r/blackfire/blackfire
[mailhog/mailhog]: https://hub.docker.com/r/mailhog/mailhog
[phpmyadmin/phpmyadmin]: https://hub.docker.com/r/phpmyadmin/phpmyadmin
[selenium/standalone-chrome]: https://hub.docker.com/r/selenium/standalone-chrome
[wodby/adminer]: https://hub.docker.com/r/wodby/adminer
[wodby/apache]: https://github.com/wodby/apache
[wodby/drupal-node]: https://github.com/wodby/drupal-node
[wodby/drupal-php]: https://github.com/wodby/drupal-php
[wodby/drupal]: https://github.com/wodby/drupal
[wodby/elasticsearch]: https://github.com/wodby/elasticsearch
[wodby/kibana]: https://github.com/wodby/kibana
[wodby/mariadb]: https://github.com/wodby/mariadb
[wodby/memcached]: https://github.com/wodby/memcached
[wodby/nginx]: https://github.com/wodby/nginx
[wodby/node]: https://github.com/wodby/node
[wodby/opensmtpd]: https://github.com/wodby/opensmtpd
[wodby/postgres]: https://github.com/wodby/postgres
[wodby/redis]: https://github.com/wodby/redis
[wodby/rsyslog]: https://hub.docker.com/r/wodby/rsyslog
[wodby/solr]: https://github.com/wodby/solr
[wodby/varnish]: https://github.com/wodby/varnish
[wodby/webgrind]: https://hub.docker.com/r/wodby/webgrind
[wodby/xhprof]: https://hub.docker.com/r/wodby/xhprof
