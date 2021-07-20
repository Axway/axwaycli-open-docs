---
title: Quick start
linkTitle: Quick start
description: Install the Axway CLI or upgrade from the Amplify CLI and start using the CLI and its components. 
weight: 10
date: 2021-07-09
---

The quick start includes details on installing the {{% variables/axway_cli_prod_name %}} and the {{% variables/axway_cli_prod_name %}} components.

## Installation

To install the {{% variables/axway_cli_prod_name %}}, run the following from the terminal:

```bash
npm i -g axway
```

Some Linux and macOS systems require elevated filesystem access to install the {{% variables/axway_cli_prod_name %}} in the global location and require `npm` to be run as sudo:

```bash
sudo npm i -g axway
```

If you experience any issues, refer to the [troubleshooting](/docs/troubleshooting/#installation-issues) page.

## Upgrading from Amplify CLI

As always we seek to provide the best solutions possible to help you achieve your business needs. The {{% variables/axway_cli_prod_name %}} (2.0.0 and later) replaces the Amplify CLI (1.5.x and earlier) and provides a richer feature set with a more robust experience.

We have added some new features:

* Completed a major user experience overhaul, used a consistent user interface (style guide), and improved the verbiage
* Added HTTP and HTTPS proxy support
* Improved command help with more detailed information
* Improved package search with keyword support
* Improved org switching experience

And improved the user experience:

* Created the Amplify SDK to improve the Platform authentication process
* Discontinued support for older Node. js versions to better align with versions supported by the [Node.js project](https://nodejs.org/en/)
* Removed the unnecessary duplicate org login prompt when user is already logged in during interactive login
* Directs users correctly to the Platform page instead of redirecting them to an un-styled login success page
* Removed two factor authentication to better support for Axway ID Single Sign On
* Improved account information structure and organization for authenticated accounts

With the {{% variables/axway_cli_prod_name %}} you can install and manage additional Axway command line programs for integrated experience. Refer to the [extensions](/docs/extensions/) section for a list of available CLIs and more details.

The {{% variables/axway_cli_prod_name %}} will automatically import your Amplify CLI settings. However it will not import any installed packages. You will need to manually install them again. To get a list of your installed packages, run:

```
amplify pm ls
```

For each package listed, install it under the {{% variables/axway_cli_prod_name %}} by running:

```
axway pm i <package_name>[@<version>]
```

## Getting help

The {{% variables/axway_cli_prod_name %}} has built-in help that can be accessed by passing `--help` into any command or by running:

```
axway
```

## Proxy server configuration

If you are behind a network proxy server, then you may need to set the proxy server URL by running the following command and replacing the username, password, proxy server URL, and port number.

```
axway config set network.proxy http://<username>:<password>@<proxy-server-url>:<port>
```

You will also need to configure the proxy server for `npm`:

```bash
npm config set https-proxy http://<username>:<password>@<proxy-server-url>:<port>
```

Refer to the [configuration](/docs/configuration/) page for more information.

## Proxy server with self-signed certificate

If your proxy server uses a self-signed TLS/SSL certificate, then you will need to disable certificate validation:

```
axway config set network.strictSSL false
```

Also disable the certificate for `npm`:

```bash
npm config set strict-ssl false
```

## Authentication

To log into the Amplify Platform, run:

```
axway auth login
```

Refer to the [authentication](/docs/authentication) page for more information.

## Packages

The {{% variables/axway_cli_prod_name %}} package manager allows you to search, view, install, update, and uninstall packages such as other {{% variables/axway_cli_prod_name %}} products.

To search for a package, run:

```
axway pm search
```

To install a package, run:

```
axway pm install <package>[@<version>]
```

To list installed packages, run:

```
axway pm list
```

Refer to the [package management](/docs/package_management/) page for more information.
