---
title: View and change user settings
linkTitle: View and change user settings
weight: 30
date: 2021-07-09
---

You must authenticate into a platform account to use the `user` command. If your platform account is not the default account, you need to pass in the `--account` argument or set your platform account as the default for your session using the `axway auth switch` command.

## Usage

```
axway user

axway user <command> [--account <name>] [options]
```

## Commands

* `activity` - Display user's activity
* `credentials` - Open a web browser to the change your password page
* `update` - Change your information
* `view` - Display user information

### activity

Displays user events such as role changes and security related events.

```
axway user activity [--from YYYY-MM-DD] [--to YYYY-MM-DD]
```

#### activity options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--from <date>` - The start date in ISO format. Defaults to 14 days from today.
* `--json` - Outputs the activity as JSON.
* `--to <date>` - The end date in ISO format. Defaults to today.

### credentials

Opens a web browser to the change your password page.

```
axway user credentials
```

### update

Allows a user to change their first name, last name, and phone number.

```
axway user update [--firstname <value>] [--lastname <value>] [--phone <value>]
```

#### update options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--firstname <value>` - The first name to set.
* `--json` - Outputs the activity as JSON.
* `--lastname <value>` - The last name to set.
* `--phone <value>` - The phone number to set.

### view

Displays the user's account information.

```
axway user view
```

#### view options

* `--account <name>` - The account to use. Defaults to the selected account.
* `--json` - Outputs the activity as JSON.
