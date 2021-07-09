---
title: Axway cli release notes
linkTitle: Axway cli release notes
description: ADD A DESCRIPTION
weight: 80
date: 2021-07-09
---

{{% variables/axway_cli_prod_name %}} 2.1.0 GA - 11 May 2021 is a minor release that includes new features, improvements, and bug fixes.

## Installation

```
npm i -g axway
```

## New Features

* cli: Display welcome and next steps after installing the {{% variables/axway_cli_prod_name %}}.
* oum: Initial release of the org, user, & team management CLI.
* auth: Publicly expose `axway auth whoami` command.
* auth: Improved handling of headless environments (Docker containers, SSH, etc).
* auth: Autodetect if headless and force token store type to "file" instead of "secure".
* general: Display feedback when launching the web browser.
* pm: Show the command to use the newly installed CLI extensions.

## Improvements

* auth: Gracefully handle fetch Axway ID user info request failures.
* auth: Handle authentication when Axway ID does not return a refresh token.
* auth: Updated secure token store dependency `keytar` resulting in no longer needing to install it at runtime.
* auth: Added environment name to list of authenticated accounts.
* general: Properly output errors when `--json` flag is set.
* general: Added deprecation warning for Node.js 10 and older. Node.js 10 support will be removed in {{% variables/axway_cli_prod_name %}} 3.0.0.
* general: Improved help screens by adding examples and consistent wording.
* pm: Show package name and version during update install steps.

For a complete list of changes, please refer to the developer [changelog](https://github.com/appcelerator/amplify-tooling/blob/master/docs/Release%20Notes/Axway%20CLI%202.1.0.md).
