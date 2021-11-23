---
title: Authentication
linkTitle: Authentication
description: Use the Axway CLI auth command to authenticate with the Amplify platform.
weight: 20
date: 2021-07-09
---

The {{% variables/axway_cli_prod_name %}} `auth` command allows you to authenticate with the {{% variables/platform_prod_name %}} under one or more accounts and switch between them. You can log in using your platform account as well as one or more [service accounts](https://docs.axway.com/bundle/axwaycli-open-docs/page/docs/authentication/service_accounts/index.html) at the same time.

To log in using a platform account, a desktop web browser is required. Headless environments, such as a SSH terminal, are not supported when authenticating into platform accounts.

A service account can be used for both desktop and headless environments. However, if authenticating in a headless environment, you must set the token store type to "file":

```
axway config set auth.tokenStoreType file
```

## Usage

```
axway auth <command> [options]
```

## Commands

* `ls`, `list` - List all authenticated accounts
* `login` - Log in to the Amplify platform
* `logout` - Log out of all or specific accounts
* `switch` - Select default account and organization
* `whoami` - Display info for an authenticated account

### ls, list

Displays a list of all authenticated accounts, their selected platform organization, and the current team.

```
axway auth ls [options]

axway auth list [options]
```

#### ls, list options

* `--json` : Outputs accounts as JSON

### login

Authenticates the {{% variables/axway_cli_prod_name %}} with the {{% variables/platform_prod_name %}} as either a platform account or service account.

You can simultaneously log into a platform account (via the web browser) as well as multiple platform and service accounts using distinct client IDs.

Once authenticated, the account's current team is set to its configured default team to use for "axway" commands.

```
axway auth login [options]
```

#### login options - general

* `--client-id`  - The CLI specific client ID
* `--force` - Re-authenticate even if the account is already authenticated
* `--json` - Outputs authenticated account as JSON
* `--no-launch-browser` - Display the authentication URL instead of opening it in the default web browser

#### login options - service account

* `-c`, `--client-secret <key>` - The service account's client secret key
* `-p`, `--password <pass>` - Your Platform Tooling password; requires `--client-secret` or `--secret-file`
* `-s`, `--secret-file <path>` - Path to the PEM formatted private key
* `-u`, `--username <email>` - Your email address used to log into the {{% variables/platform_prod_name %}}; requires `--client-secret` or `--secret-file`

### Platform accounts

A platform account allows you to manage organizations, teams, and your user account. There are two ways to authenticate into a platform account.

#### Proof Key for Code Exchange (PKCE)

PKCE is the default authentication method. It will open a web browser to the {{% variables/platform_prod_name %}} login page.

```
axway auth login
```

### Service account with username/password

Authenticate headlessly without needing to launch a web browser. You must specify either a Client Secret or a PEM formatted private key along with your Platform Tooling Credentials. You will also need to know your service account's Client ID such as "DOSA_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx".

Your username is your email address. You can set or change your password on the Tooling Credentials page: [https://platform.axway.com/#/user/credentials](https://platform.axway.com/#/user/credentials). For more information, refer to [Configuring tooling credentials](https://docs.axway.com/bundle/platform-management/page/docs/management_guide/configuring_and_managing_identity_providers/configuring_tooling_credentials/index.html).

```
axway auth login --client-id <id> --client-secret <key> --username <email>
```

Or

```
axway auth login --client-id <id> --secret-file /path/to/pem/file -username <email>
```

The commands above will prompt you for your password. You may also specify `--password <pass>` for a non-interactive login.

### Service accounts

With a service account, you can headlessly authenticate using a Client Secret or a PEM formatted private key. Service accounts are not able to perform certain actions such as organization and team management.

For additional options on configuring or authentication with service accounts, refer to [Service accounts](https://docs.axway.com/bundle/axwaycli-open-docs/page/docs/authentication/service_accounts/index.html).

#### Client service key

```
axway auth login --client-id <id> --client-secret <key> --username <email>
```

### PEM formatted private key

```
axway auth login --client-id <id> --secret-file /path/to/pem/file -username <email>
```

#### Authentication expiration

Upon logging in, you are granted an access token which expires after 30 minutes.

If you logged in using the web browser authentication flow (PKCE), the Axway CLI will receive a refresh token that expires after 6 hours. The {{% variables/axway_cli_prod_name %}} will use this refresh token to automatically refresh an expired access token. If more than 6 hours has elapsed, then the authenticated account will become invalidated and you must log in again.

### logout

Revokes access tokens for one, multiple, or all accounts.

```
axway auth logout [options] [<accounts...>]
```

#### logout options

* `--json` - Outputs revoked accounts as JSON

### switch

Once authenticated, you can set the default account, organization, and current team to use for `axway` commands.

Only platform accounts have organizations. If the selected account is a service account, then the organization selection is skipped.

Changing the current team will only affect your local machine and does not change the actual default team.

```
axway auth switch [options]
```

#### switch options

* `--account <name>` - The account to switch to
* `--json` - Outputs selected account as JSON
* `--org <id|guid|name>` - The platform organization to switch to
* `--team <guid|name>` - The team to use for the selected account

### whoami

Display the currently selected account, organizations, roles, and teams.

```
axway auth whomai
```

#### whoami options

* `--json` - Outputs accounts as JSON
