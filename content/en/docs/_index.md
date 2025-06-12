---
title: Axway CLI
linkTitle: Axway CLI
weight: 10
date: 2021-07-09
---

The Axway CLI (Command Line Interface) is a framework that provides a single CLI entry point for common functionality of the Amplify platform. The framework provides authentication to Amplify, organization and user management and package management. Packages are extensions to the Axway CLI that extend the functionality of the CLI by providing features for additional services provided by the Amplify platform. The following are the available packages:

* [Axway Central CLI](https://docs.axway.com/bundle/amplify-central/page/docs/integrate_with_central/cli_central/index.html) (documented in the Axway Central CLI guide)
* [Axway Edge Agent CLI](/docs/extensions/axway_edge_agent_cli/)
* [Axway Repository CLI](/docs/extensions/axway_repository_cli/)
* [{{% variables/apibuilder_prod_name %}} CLI](https://docs.axway.com/bundle/api-builder/page/docs/developer_guide/cli/index.html) (documented in the {{% variables/apibuilder_prod_name %}} 4.x guide)

## Overview

With the {{% variables/axway_cli_prod_name %}} you can:

* Install and manage additional Axway command line programs
* Authenticate against the Amplify API Management Platform
* Manage organizations, users, and teams
* Create service accounts for headless environments
* Automate {{% variables/axway_cli_prod_name %}} commands from other scripting languages
* Choose any authenticated account per command

## Prerequisites

Axway CLI supports the following platforms:

| Axway CLI Version | Operating System |
| --- | --- |
| 2.x - 3.x | Linux (64-bit) |
| 2.x | Linux (32-bit) |
| 2.x - 3.x | macOS (64-bit) |
| 2.x - 3.x | Windows (64-bit) |
| 2.x | Windows (32-bit) |

The system requirements are:

| Component | Version |
| --- | --- |
| [Node.js](https://nodejs.org/) | 20.18.2 LTS or later |
| npm | 10.8.2 or later |

{{% alert title="Note" color="primary" %}}Operating systems and architecture support varies across {{% variables/axway_cli_prod_name %}} products. Refer to each product's requirements for more information.{{% /alert %}}

## Next Steps

Install the {{% variables/axway_cli_prod_name %}} and follow the [quick start](/docs/quick_start/) guide.
