---
title: Manage teams
linkTitle: Manage teams
weight: 20
date: 2021-07-09
---

The {{% variables/axway_cli_prod_name %}} `team` command allows you to create teams, manage team users, and view team information.

You must authenticate into a platform account to use the `team` command. If your platform account is not the default account, you need to pass in the `--account` argument or set your platform account as the default for your session using the `axway auth switch` command.

## Usage

```
axway team

axway team <command> [--account <name>] [options]
```

## Commands

* `add` - Add a team to an organization
* `ls`, `list` - List organization teams
* `rm`, `remove` - Remove a team from an organization
* `update` - Update team information
* `user` - Manage team users
    * `add` - Add a new user to a team
    * `ls`, `list` - List all users in a team
    * `rm`, `remove` - Remove a user from a team
    * `roles` - View available user organization roles
    * `update` - Update an user's team roles
* `view` - View team information

### add

Adds a team to an organization.

```
axway team add <org> <team_name> [options]
```

You may specify the organization by name or guid. Use double quotes around the team name if the name has spaces or special characters.

#### add options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--default` - Set the team as the default team.
* `--desc <value>` - The description of the team.
* `--json` - Outputs the activity as JSON.
* `--tag <tag>` - One or more tags to assign to the team.

### ls, list

Lists organization teams.

```
axway team ls [<org>]

axway team list [<org>]
```

By default, the `list` command will use your currently selected organization. To show usage for a specific organization, pass in an organization name or guid.

#### ls, list options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the list of organizations as JSON.

### rm, remove

Removes a team from an organization.

```
axway team remove <org> <team>
```

You may specify the organization by name or guid. Specify the team by its guid.

#### rm, remove options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### update

Updates team information such as whether the team is the default, the team name, the description, and the associated tags.

```
axway team update <org> <team> [options]
```

You may specify the organization by name or guid. Specify the team by its guid.

#### update options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--default` - Set the team as the default team.
* `--desc <value>` - The description of the team.
* `--json` - Outputs the activity as JSON.
* `--name <value>` - The team name.
* `--tag <tag>` - One or more tags to assign to the team.

### user

Displays the help screen for managing team users.

```
axway team user
```

### user add

Adds a user to an organization.

```
axway team user add <org> <email> --role <platform_role> --role <additional_role>
```

The `user add` command requires an organization name or guid, the email address or guid of the user to add, and one or more roles.

The user must already be a platform user.

An team user must be assigned a platform role and optionally a product specific role. You may specify the roles with multiple `--role "role"`  options or a single `--role "role1,role2,role3"`  option with a comma-separated list of roles. To view available user roles, run: `axway team user roles`.

#### user add options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.
* `--role <role>` - Assign one or more organization roles to a user.

### user list

Lists all users in a team.

```
axway team user list <org>
```

You may specify the organization by name or guid.

#### user list options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### user remove

Removes a user from a team.

```
axway team user remove <org> <team> <user>
```

You may specify the organization by name or guid as well as specify the team by guid and user by email address or guid.

#### user remove options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### user roles

Displays all available users roles at the team level.

```
axway team user roles
```

#### user roles options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.

### user update

Updates a user's team roles.

```
axway team user update <org> <team> <user> --role <platform_role> --role <additional_role>
```

The `user update` command requires an organization name or guid, a team guid, the email address or guid of the user to update, and one or more roles.

An organization user must be assigned a platform role and optionally a product specific role. You may specify the roles with multiple `--role "role"`  options or a single `--role "role1,role2,role3"`  option with a comma-separated list of roles. To view available user roles, run: `axway team user roles`.

#### user update options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the result as JSON.
* `--role <role>` - Assign one or more team roles to a user.

### view

Displays information about a team.

```
axway team view <org> <team>
```

You may specify the organization by name or guid. Specify the team by its guid.

#### view options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the organization information as JSON.
