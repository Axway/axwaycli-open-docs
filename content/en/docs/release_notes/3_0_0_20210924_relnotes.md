---
title: Axway CLI 3.0.0 GA release notes - 24 Sep 2021
linkTitle: Axway CLI 3.0.0 GA release notes - 24 Sep 2021
description: Review Axway CLI release details such as new features, improvements, breaking changes, and bug fixes.
weight: 10
date: 2021-09-24
---

{{% variables/axway_cli_prod_name %}} 3.0.0 GA - 24 Sep 2021 is a major release that includes new features, improvements, breaking changes, and bug fixes.

## Installation

```
npm i -g axway
```

## Breaking Changes

* general: Require Node.js 12.13.0 LTS or newer.

## New Features

* auth: Added `service-account` command for creating and managing service accounts.
* cli: Added `telemetry` to help improve Axway products.
* oum: Added support to activity and usage commands for selecting a date range by month.

## Improvements

* auth: Removed `--client-id` from all auth commands except `login` because it was unused.
* config: Only error out when config file is bad when running a config command.
* oum: Renamed `axway team add` command to `axway team create`. Note that `add` will continue to work.
* oum: Always show teams section for `axway org view` even if there are no teams.
* pm: Fixed filtering package properties when running `axway pm view <pkg>` and outputting as JSON.

For a complete list of changes, please refer to the developer [changelog](https://github.com/appcelerator/amplify-tooling/blob/master/docs/Release%20Notes/Axway%20CLI%203.0.0.md).
