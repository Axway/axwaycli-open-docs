---
title: Axway Repository CLI
linkTitle: Axway Repository CLI
description: ADD A DESCRIPTION
weight: 20
date: 2021-07-09
---

The Axway Repository CLI is used to manage Docker images and Helm charts stored in the Axway repository.

## Installation

To install the Axway Repository CLI, run the following from the terminal:

```
axway pm install @axway/axway-repository-cli
```

## Getting started

To get a list of the available Axway Repository commands, run the following.

```
axway repo
```

Axway repo is the alias for:

```
axway repository
```

The Axway Repository CLI includes Docker and Helm repository types.

## Docker

The Axway Repository CLI allows you to list, pull, register, search, and unregister Docker images from the Axway Repository. The Axway Repository CLI requires that you have [Docker](https://docs.docker.com/get-docker/) installed natively on your local machine to use the Docker commands.

To get a list of all available Docker commands, run:

```
axway repository docker
```

## Docker usage

```
axway repository docker <command> [options]
```

## Docker commands

* `ls, list` - List all available Axway Repository images
* `pull` - Pull an image from Axway Repository
* `r, register` - Register the Axway Docker repository to your local native Docker CLI
* `search` - Search the Axway Repository for images
* `u, unregister` - Unregister the Axway Docker repository to your local native Docker CLI

### ls, list

Displays a list of all Docker images.

```
axway repository docker ls [options]
```

#### ls, list options

* `--full-names` - Show full image names

#### ls, list example

```
IMAGE                                           PRODUCT          TITLE                                DESCRIPTION

securetransport-prod/5.5/hello-world:latest     SecureTransport  Test title                           lorem ipsum

securetransport-prod/4.5.1/demo:latest          SecureTransport  Test title                           test description
securetransport-prod/4.5.1/demo1:latest         SecureTransport  1                                    1

securetransport-prod/5.5/docker_image_1:latest  SecureTransport  Secure Transport v. 5.5 -UPDATED rr  Lorem ipsum dolor sit amet, consec...
securetransport-prod/1.2/docker_image_1:latest  SecureTransport  test asdf
```

### pull

Pulls a Docker image.

```
axway repository docker pull
```

#### pull usage

```
axway repository docker pull [options] <image>
```

**
pull arguments**

* `--image` - Docker image name

### r, register

Registers the Axway Docker repository to your local native Docker CLI.

To use the {{% variables/axway_cli_prod_name %}}, you must run the following command first:

```
axway repository docker register
```

This registers `http://docker.repository.axway.com`to your local Docker as the Docker registry and authenticates you on your local Docker CLI.

### search

Searches for a Docker image.

```
axway repository docker search
```

#### search usage

```
axway repository docker search [options] <term>
```

#### search arguments

* `--term` - The image name

#### search options

* `--full-names` - Show image full names
* `--limit` - Max number of search results
* `--offset` - Retrieving search results with offset pagination

#### search example

```
$ axway repository docker search api

Available entries: 1

IMAGE            PRODUCT          TITLE                           DESCRIPTION
5.5/hello-world  SecureTransport  API Hello world TEST FROM CHAI abv  SecureTransport Docker sfsdf d gfd...
```

### u, unregister

Unregisters the Axway Docker repository to your local native Docker CLI.

```
axway repository docker unregister
```

This reverses registering [http://docker.repository.axway.com](http://docker.repository.axway.com) to your local Docker as the Docker registry and authenticating you on your local Docker CLI.

## Helm

Helm uses a packaging format called charts. A chart is a collection of files that describe a related set of Kubernetes resources. The Axway Repository CLI allows you to list, pull, register, search, and unregister Helm charts from the Axway Repository. The Axway Repository CLI requires that you have [Helm](https://helm.sh/docs/intro/install/) installed natively on your local machine to use the Helm commands.

To get a list of all available Helm commands, run:

```
axway repository helm
```

## Helm usage

```
axway repository helm <command> [options]
```

## Helm commands

* `ls, list` - List all available Axway Repository Helm charts
* `pull` - Pull a Helm chart from the Axway Repository
* `r, register` - Register the Axway Helm repository to your local native Helm CLI
* `search` - Search in the Axway Repository
* `u, unregister` - Unregister the Axway Helm repository to your local native Helm CLI

### ls, list

Lists all available Axway Repository Helm charts.

```
axway repository helm ls
```

#### ls, list example

```
Available entries: 1

NAME                               CHART  PRODUCT          TITLE           DESCRIPTION
helm-securetransport-prod-grafana  6.1.4  SecureTransport  helm updated 3  helm updated
```

### pull

Pulls a Helm chart from the Axway Repository.

```
axway repository helm pull
```

#### pull usage

```
axway repository helm pull [options] <chartname>
```

#### Helm arguments

* `--chartname` - Helm chart name

### r, register

Registers the Axway Helm repository to your local native Helm CLI.

To use the {{% variables/axway_cli_prod_name %}}, you must run the following command first:

```
axway repository helm register
```

This registers [http://helm.repository.axway.com](http://helm.repository.axway.com) to your local Helm as the Helm registry and authenticates you on your local Helm CLI.

### search

Searches in the Axway Repository.

```
axway repository helm search
```

#### search usage

```
axway repository helm search [options] <term>
```

#### search arguments

* `--term` - The Helm chart name

#### search options

* `--full-names` - Show image full names
* `--limit` - Max number of search results
* `--offset` - Retrieving search results with offset pagination

#### search example

```
$ axway repository helm search api

Available entries: 1

NAME     PRODUCT          TITLE               DESCRIPTION
grafana  SecureTransport  API helm updated 3  helm updated
```

### u, unregister

Unregisters the Axway Helm repository to your local native Helm CLI.

```
axway repository helm unregister
```

This reverses registering [http://helm.repository.axway.com](http://helm.repository.axway.com) to your local Helm as the Helm registry and authenticating you on your local Helm CLI.
