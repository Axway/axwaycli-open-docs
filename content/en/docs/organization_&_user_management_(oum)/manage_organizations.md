---
title: Manage organizations
linkTitle: Manage organizations
description: Use the Axway CLI org command to manage Platform organizations.
weight: 10
date: 2021-07-09
siblings_only: true
---

The {{% variables/axway_cli_prod_name %}} `org` command allows you to rename the organization, manage organization users, and view organization information.

You must authenticate into a platform account to use the `org` command. If your platform account is not the default account, you need to pass in the `--account` argument or set your platform account as the default for your session using the `axway auth switch` command.

## Usage

```
axway org

axway org <command> [--account <name>] [options]
```

## Commands

* `activity` - Display organization activity report
* `idp` - Manage organization identity provider settings
* `ls`, `list` - List organizations
* `rename` - Rename an organization
* `usage` - Display organization usage report
* `user` - Manage organization users
    * `add` - Add a new user to an organization
    * `ls`, `list` - List all users in an organization
    * `rm`, `remove` - Remove a user from an organization
    * `roles` - View available organization user roles
    * `update` - Update an user's organization roles
* `view` - View organization information

### activity

Displays organization events such as organization changes and security related events.

```
axway org activity [<org>] [--from YYYY-MM-DD] [--to YYYY-MM-DD]
```

By default, the `activity` command will use your currently selected organization. To show activity for a specific organization, pass in an organization name or guid.

#### activity options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--from <date>` - The start date in ISO format. Defaults to 14 days from today.
* `--json` - Outputs the activity as JSON.
* `--to <date>` - The end date in ISO format. Defaults to today.

### idp

Opens the web browser to the identity provider settings page for the specified organization.

```
axway org idp [<org>]
```

By default, the `idp` command will use your currently selected organization. To manage the identity provider settings for a specific organization, pass in an organization name or guid.

#### idp options

* `--account <name>` - The account to use. Defaults to the selected account.

### ls, list

Lists all associated organizations for the current authenticated platform account.

```
axway org ls

axway org list
```

#### ls, list options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the list of organizations as JSON.

### rename

Renames an organization.

```
axway org rename <org> <new_name>
```

You may specify the organization by name or guid. Use double quotes around the new organization name if the name has spaces or special characters.

#### rename options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### usage

Displays organization usage such as the number of API calls and push notifications.

```
axway org usage [<org>] [--from YYYY-MM-DD] [--to YYYY-MM-DD]
```

By default, the `usage` command will use your currently selected organization. To show usage for a specific organization, pass in an organization name or guid.

#### usage options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--from <date>` - The start date in ISO format. Defaults to 14 days from today.
* `--json` - Outputs the usage as JSON.
* `--to <date>` - The end date in ISO format. Defaults to today.

### user

Displays the help screen for managing organization users.

```
axway org user
```

### user add

Adds or invites a user to an organization.

```
axway org user add <org> <email> --role <platform_role> --role <additional_role>
```

The `user add` command requires an organization name or guid, the email address of the user to add, and one or more roles.

If the user is not already a platform user, they will automatically be invited to create a platform account and join the organization.

An organization user must be assigned a platform role and optionally a product specific role. You may specify the roles with multiple `--role "role"`  options or a single `--role "role1,role2,role3"`  option with a comma-separated list of roles. To view available user roles, run: `axway org user roles`.

#### user add options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.
* `--role <role>` - Assign one or more organization roles to a user.

### user list

Lists all users for a specific organization.

```
axway org user list <org>
```

By default, the `user list` command will use your currently selected organization. To show activity for a specific organization, pass in an organization name or guid.

#### user list options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### user remove

Removes a user from an organization.

```
axway org user remove <org> <user>
```

You may specify the organization by name or guid as well as specify the user by email address or guid.

#### user remove options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### user roles

Displays all available users roles at the organization level.

```
axway org user roles
```

#### user role options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### user update

Updates a user's organization roles.

```
axway org user update <org> <email> --role <platform_role> --role <additional_role>
```

The `user update` command requires an organization name or guid, the email address or guid of the user to update, and one or more roles.

An organization user must be assigned a platform role and optionally a product specific role. You may specify the roles with multiple `--role "role"`  options or a single `--role "role1,role2,role3"`  option with a comma-separated list of roles. To view available user roles, run: `axway org user roles`.

#### user update options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.
* `--role <role>` - Assign one or more organization roles to a user.

### view

Displays information about an organization.

```
axway org view [<org>]
```

By default, the `view` command will use your currently selected organization. To show usage for a specific organization, pass in an organization name or guid.

#### view options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the organization information as JSON.
