---
title: Axway cli package management
linkTitle: Axway cli package management
description: ADD A DESCRIPTION
weight: 50
date: 2021-07-09
---

The {{% variables/axway_cli_prod_name %}} `pm` command allows you to manage, install, and uninstall packages.

## Usage

```
axway pm <command> [options]
```

## Commands

* `i`, `install` - Install a specific package

* `ls`, `list` - List all installed accounts
* `purge` - Remove all non-active packages
* `s`, `search` - Search registry for packages
* `rm`, `uninstall` - Remove the specified package
* `update` - Download updates for installed packages
* `use` - Activate a specific package version
* `v`, `view` - Display info for a specific package

### i, install

Installs a package. Multiple versions of the same package may be installed simultaneously. Run the `use` command (see below) to choose which version is active.

```
axway pm install [options] <name>[@<version>]
```

**Options**

* `--json` - Outputs installed package as JSON

### ls, list

Displays a list of all installed packages.

```
axway pm list [options]
```

**Options**

* `--json` - Outputs accounts as JSON

### purge

Uninstalls all non-active, managed packages. This is useful after installing a newer version or running the `update` command. Note that only managed packages, packages that were installed via the {{% variables/axway_cli_prod_name %}} package manager, will be removed.

```
axway pm purge [options] [<package>]
```

**Options**

* `--json` - Outputs purged packages as JSON

### s, search

Searches the registry for a package. If no search criteria is specified, every package in the registry is returned.

```
axway pm search [options] [<keyword>]
```

**Options**

* `--json` - Outputs packages as JSON
* `--repository <repo>` - The originating repository
* `--type <type>` - The type of package

Currently, the only supported repository is `"npm"`.

Available package types include `"amplify-cli-plugin"` and `"central-cli-plugin"`.

### rm, uninstall

Removes a single or all versions of a package.

```
axway pm uninstall [options] <package>[@<version>]
```

If no `version` is specified, then all versions of the package are removed.

**Options**

* `--json` - Outputs removed packages as JSON

### update

Checks for package updates, then downloads, installs, and marks them as active.

```
axway pm update [options]
```

**Options**

* `--json` - Outputs updated packages as JSON

### use

Activates a specific package version. This is useful when multiple versions of a package are installed.

```
axway pm use [options] <package>[@<version>]
```

If no `version` is specified, then it will default to the `"latest"` version.

**Options**

* `--json` - Outputs activated package as JSON

### v, view

Displays information about a package from the registry.

```
axway pm view [options] <package>[@<version] [<filter>]
```

If no `version` is specified, then it will default to the `"latest"` version.

The `filter` argument is used to display a specific field such as `"name"` or `"version"`.

**Options**

* `--json` - Outputs package info as JSON
