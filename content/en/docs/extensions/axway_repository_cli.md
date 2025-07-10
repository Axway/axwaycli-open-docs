---
title: Axway Repository CLI
linkTitle: Axway Repository CLI
weight: 20
date: 2021-07-09
---

Use the Axway Repository CLI extension to the Axway CLI to manage Docker images, Helm charts, and files stored in the Axway Central Repository.

## Installation

To install the Axway Repository CLI, run the following from the terminal:

```sh
axway pm install @axway/axway-repository-cli
```

## Getting started

To get a list of the available Axway Repository commands, run the following.

```sh
axway repo
```

Axway repo is the alias for:

```sh
axway repository
```

The Axway Repository CLI includes Docker, Helm, and binary repository types.

## Docker

The Axway Repository CLI allows you to list, pull, register, search, and unregister Docker images from the Axway Repository. The Axway Repository CLI requires that you have [Docker](https://docs.docker.com/get-docker/) installed natively on your local machine to use the Docker commands.

To get a list of all available Docker commands, run:

```sh
axway repository docker
```

## Docker usage

```sh
axway repository docker <command> [options]
```

## Docker commands

* `ls, list` - List all available Axway Repository images
* `pull` - Pull an image from Axway Repository
* `r, register` - Register the Axway Docker repository to your local native Docker CLI
* `search` - Search the Axway Repository for images
* `u, unregister` - Unregister the Axway Docker repository to your local native Docker CLI

### Docker ls, list

Displays a list of all Docker images.

```sh
axway repository docker ls [options]
```

#### Docker ls, list options

* `--offset [value]` - Retrieving results with offset
* `--limit [value]` - Maximum number of results (up to 300)

#### Docker ls, list example

```
Entries: 7; Limit: 30; Offset: 0

IMAGE                                                                                     PRODUCT                    TITLE         DESCRIPTION
docker.repository-dev.axwaytest.net/securetransport-prod/5.5/ucs-controller:rs            SecureTransport            adada         1 azerty
docker.repository-dev.axwaytest.net/docker-test-34/apimanagement/anm2:5                   Test Firewall/Secure Msgr  23test        Lorem ipsum dolor sit amet, consec...
docker.repository-dev.axwaytest.net/securetransport-prod/5.5/ucs-controller:APIGOV-16522  SecureTransport            1             1 qwerty
docker.repository-dev.axwaytest.net/docker-test-34/apimanagement/anm2:5                   Test Firewall/Secure Msgr  11889 23test  zLorem ipsum dolor sit amet, conse...
docker.repository-dev.axwaytest.net/docker-test-3/apimanagement/anm2:@42                  Test Firewall/Secure Msgr  23test        Lorem ipsum dolor sit amet, consec...
docker.repository-dev.axwaytest.net/docker-test-34/apimanagement/anm2:5                   Test Firewall/Secure Msgr  23test        Lorem ipsum dolor sit amet, consec...
docker.repository-dev.axwaytest.net/docker-test-3/apimanagement/anm:7.6.3                 Test Firewall/Secure Msgr  test          Lorem ipsum dolor sit amet, consec...
```

### Docker pull

Pulls a Docker image.

```sh
axway repository docker pull
```

#### Docker pull usage

```sh
axway repository docker pull [options] <image>
```

#### Docker pull arguments

* `--image` - Docker image name

### Docker r, register

Registers the Axway Docker repository to your local native Docker CLI.

To use the {{% variables/axway_cli_prod_name %}}, you must run the following command first:

```sh
axway repository docker register
```

This registers the Docker repository, located on <https://repository.axway.com>, to your local Docker as the Docker registry and authenticates you on your local Docker CLI.

### Docker search

Searches for a Docker image.

```sh
axway repository docker search
```

#### Docker search usage

```sh
axway repository docker search [options] <term>
```

#### Docker search arguments

* `--term` - The image name

#### Docker search options

* `--offset [value]` - Retrieving search results with offset
* `--limit [value]` - Maximum number of search results (up to 300)

#### Docker search example

```
$ axway repository docker search api

Available entries: 1

IMAGE            PRODUCT          TITLE                               DESCRIPTION
5.5/hello-world  SecureTransport  API Hello world TEST FROM CHAI abv  SecureTransport Docker sfsdf d gfd...
```

### Docker u, unregister

Unregisters the Axway Docker repository to your local native Docker CLI.

```sh
axway repository docker unregister
```

This reverses registering the Docker repository, located on <https://repository.axway.com>, from your local Docker CLI.

## Helm

Helm uses a packaging format called charts. A chart is a collection of files that describe a related set of Kubernetes resources. The Axway Repository CLI allows you to list, pull, register, search, and unregister Helm charts from the Axway Repository. The Axway Repository CLI requires that you have [Helm](https://helm.sh/docs/intro/install/) installed natively on your local machine to use the Helm commands.

To get a list of all available Helm commands, run:

```sh
axway repository helm
```

## Helm usage

```sh
axway repository helm <command> [options]
```

## Helm commands

* `ls, list` - List all available Axway Repository Helm charts
* `pull` - Pull a Helm chart from the Axway Repository
* `r, register` - Register the Axway Helm repository to your local native Helm CLI
* `search` - Search in the Axway Repository
* `u, unregister` - Unregister the Axway Helm repository to your local native Helm CLI

### Helm ls, list

Lists all available Axway Repository Helm charts.

```sh
axway repository helm ls
```

#### Helm ls, list options

* `--offset [value]` - Retrieving results with offset
* `--limit [value]` - Maximum number of results (up to 300)

#### Helm ls, list example

```
Available entries: 1

NAME                               CHART  PRODUCT          TITLE           DESCRIPTION
helm-securetransport-prod-grafana  6.1.4  SecureTransport  helm updated 3  helm updated
```

### Helm pull

Pulls a Helm chart from the Axway Repository.

```sh
axway repository helm pull
```

#### Helm pull usage

```sh
axway repository helm pull [options] <chartname>
```

#### Helm arguments

* `--chartname` - Helm chart name

### Helm r, register

Registers the Axway Helm repository to your local native Helm CLI.

To use the {{% variables/axway_cli_prod_name %}}, you must run the following command first:

```sh
axway repository helm register
```

This registers the Helm repository, located on <https://repository.axway.com>, to your local Helm as the Helm registry and authenticates you on your local Helm CLI.

### Helm search

Searches in the Axway Repository.

```sh
axway repository helm search
```

#### Helm search usage

```sh
axway repository helm search [options] <term>
```

#### Helm search arguments

* `--term` - The Helm chart name

#### Helm search options

* `--full-names` - Show image full names
* `--limit` - Max number of search results
* `--offset` - Retrieving search results with offset pagination

#### Helm search example

```
$ axway repository helm search api

Available entries: 1

NAME     PRODUCT          TITLE               DESCRIPTION
grafana  SecureTransport  API helm updated 3  helm updated
```

### Helm u, unregister

Unregisters the Axway Helm repository to your local native Helm CLI.

```sh
axway repository helm unregister
```

This reverses registering the Helm repository, located on <https://repository.axway.com>, from your local Helm CLI.

## Files and packages

The Axway Repository CLI allows you to list, pull, search, and download files and packages from the Axway Central Repository.

To get a list of all available commands, run:

```sh
axway repository file
```

## Files usage

```sh
axway repository file <command> [options]
```

## Files commands

* `i, info` - Detailed information about a file or a package
* `ls, list` - List all available Axway Repository files and packages
* `p, pull` - Download Axway Repository file or package
* `s, search` - Search in Axway Repository

### Files ls, list

Displays a list of all Docker images.

```sh
axway repository file ls [options]
```

#### Files ls, list options

* `--offset [value]` - Retrieving results with offset
* `--limit [value]` - Maximum number of results (up to 300)

#### Files ls, list example

```
ID                                    TITLE                                                              TYPE              PRODUCT               VERSION  STATUS  DATE
2c7948e2-9ddb-4728-ab4d-10aa5b663f1c  SecureTransport 4.9.0 (allOS) updated                              ProductExtension  SecureTransport       4.9.0    GA      2020-10-22T14:37:48.000Z
3067407d-9d38-4256-977d-876458ff6840  SecureTransport 4.9.0 (aix-power-32)                               ProductExtension  SecureTransport       4.9.0    GA      2020-10-22T14:17:52.000Z
58591dc2-3d69-47da-9350-eb04e88ca75d  AccountingIntegrator 2.2.0 (linux-x86-64)                          ProductExtension  AccountingIntegrator  2.2.0    GA      2020-10-22T11:37:50.000Z
3c3fc3a5-1df0-4927-b83f-88a85248cf96  Integrator 2.1.1 FTP Communications Connector User Guide           ProductExtension  SecureTransport       5.2.1    GA      2020-09-13T10:14:43.000Z
```

### Files download/pull

Download a file or package.

```sh
axway repository file pull
```

#### Files download usage

```sh
axway repository file pull <ID> [options] [<OUTPUT>]
```

#### Files pull arguments

* `--fileid` - File unique identifier
* `--filename` - Output file name

### Files info

Get file or package additional information.

```sh
axway repository file info
```

#### Files info usage

```sh
axway repository file info <ID> [options]
```

#### Files info arguments

* `--fileid` - File unique identifier

### Files search

Searches for a file or package.

```sh
axway repository file search
```

#### Files search usage

```sh
axway repository file search <TERM> [options]
```

#### Files search arguments

* `--term` - The image name

#### Files search options

* `--offset [value]` - Retrieving search results with offset
* `--limit [value]` - Maximum number of search results (up to 300)

#### Files search example

```
$ axway repository file search api

Entries: 2272; Limit: 30; Offset: 0

ID                                    TITLE                                                                     TYPE                  PRODUCT      VERSION  STATUS  DATE
726bf0a3-8164-43cf-8488-ba4684c70a19  APIGateway 7.3.1 VMware                                                   VMWare                API Gateway  7.3.1    GA      2014-07-31T17:20:38.000Z
9d2673ea-8679-4c21-95b4-2564410e3457  APIGateway 7.3.0 VMware                                                   VMWare                API Gateway  7.3.0    GA      2014-05-12T12:17:24.000Z
82589e86-6636-46c0-99ba-a7e0a4dfcb04  API Gateway and API Manager 7.5.3 (win-x86-32)                            Install               API Manager  7.5.3    GA      2017-04-11T17:18:18.000Z
31c55b1e-6da5-45f5-9d3a-8553f822c220  API Gateway and API Manager 7.5.3 ISO (ap-x86-64)                         Appliance             API Manager  7.5.3    GA      2017-04-20T16:46:26.000Z
ec44fbdd-b879-4b01-89b7-4991a00af57c  API Gateway and API Manager 7.5.3 Install (linux-x86-64)                  Install               API Manager  7.5.3    RA      2017-04-11T16:54:54.000Z
ef5a1b9d-2508-4c2a-b072-57305aa7894e  Api Gateway Test Download                                                 UpgradePack           API Gateway  6.3.1    GA      2018-03-12T14:37:48.000Z
...
```
