---
title: Authentication
linkTitle: Authentication
description: ADD A DESCRIPTION
weight: 20
date: 2021-07-09
---

The {{% variables/axway_cli_prod_name %}} `auth` command allows you to authenticate with the Amplify Platform under one or more accounts and switch between them.

## Usage

```
axway auth <command> [options]
```

## Commands

* `ls`, `list` - Lists all authenticated accounts
* `login` - Log in to the Amplify Platform
* `logout` - Log out of all or specific accounts
* `switch` - Select default account and organization

### ls, list

Displays a list of all authenticated accounts.

```
axway auth ls [options]

axway auth list [options]
```

#### ls, list options

* `--json` : Outputs accounts as JSON

### login

Logs into the Amplify Platform using Proof Key for Code Exchange (PKCE), client secret key, or signed JSON Web Token (JWT) file.

You can be logged into multiple accounts with varying client IDs at the same time.

```
axway auth login [options]
```

#### login options

* `--client-id`  - The CLI specific client ID
* `--client-secret <key>` - A secret key issued by Axway
* `--force` - Re-authenticate even if the account is already authenticated
* `--json` - Outputs authenticated account as JSON
* `--no-launch-browser` - Display the authentication URL instead of opening it in the default web browser
* `--secret-file <path>` - Path to the PEM key issued by Axway
* `--service` - Authenticates client secret for non-platform service account

#### Proof Key for Code Exchange (PKCE)

PKCE is the default authentication method. It will open a web browser to the Amplify Platform login page.

```
axway auth login
```

#### Client Secret Key

This method requires a client secret key to be issued by Axway ID. This method is intended to be used for service accounts that are not associated to a platform account.

```
axway auth login --client-secret XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

#### Signed JWT

This method requires a signed PEM file to be issued by Axway ID. This method is intended to be used for service accounts that are not associated to a platform account.

```
axway auth login --secret-file /path/to/pem
```

#### Authentication expiration

When logging into the Amplify Platform via the web browser, you will have a web browser session and local access tokens. The web browser session will expire after a short period of inactivity in the Amplify Platform website.

The access token will expire after a short period after it has been issued. The access token will automatically renew within longer period of time since the token was issued. If too much time has passed, then the user must re-authenticate.

### logout

Revokes access tokens for one, multiple, or all accounts.

```
axway auth logout [options] [<accounts...>]
```

#### logout options

* `--json` - Outputs revoked accounts as JSON

### switch

Once authenticated into at least one account, you can set the default account and organization to use for `axway` commands.

```
axway auth switch [options]
```

#### switch options

* `--account <name>` - The account to switch to
* `--json` - Outputs selected account as JSON
* `--org <id|guid|name>` - The platform account's organization to switch to

Only platform accounts have an organizations. If the selected account is a service account, then the organization selection is skipped.
