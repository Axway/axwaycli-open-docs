---
title: 'Automation'
linkTitle: 'Automation'
description: ADD A DESCRIPTION
weight: 65
date: 2021-07-09
draft: false
---

The {{% variables/axway_cli_prod_name %}} can be used to automate tasks such as inviting users to an organization and managing teams.

## Authentication

Automation scripts need to authenticate to perform certain actions. By default, the {{% variables/axway_cli_prod_name %}} requires a web browser to authenticate. However using a service account with platform tooling credentials, a script can authenticate headlessly without needing a web browser.

There are two ways to authenticate with a service account: Client Secret and a PEM formatted private key. You will also need to know your service account's Client ID such as "DOSA_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx".

After selecting one of these methods, you then need to specify your platform tooling username and password. Your username is your email address. You can set or change your password on the Tooling Credentials page: [https://platform.axway.com/#/user/credentials](https://platform.axway.com/#/user/credentials). For more information, refer to [Configuring Tooling Credentials](https://docs.axway.com/bundle/Amplify_Platform_Management_allOS_en/page/configuring_tooling_credentials.html).

```
axway auth login --client-id <id> --secret-file /path/to/pem/file --username <email> --password <pass>
```

Or

```
axway auth login --client-id <id> --client-secret <key> --username <email> --password <pass>
```

After authenticating, your session is valid for 30 minutes. Your automation script should check the exit code for all commands being run and the session expires, you will need to re-authenticate before resuming your tasks. You may also a timer that re-authenticates around 29 minutes so that your access tokens never expire. Note that if you attempt to re-authenticate before the previous access token has expired, you need to specify the `--force` login flag.

```
# how to force a login before access token is expired
axway auth login --client-id <id> --secret-file /path/to/pem/file --username <email> --password <pass> --force
```

## Exit Codes

The {{% variables/axway_cli_prod_name %}} returns an exit code of 0 when the command completes successfully and 1 when an error occurs. If an error occurs, the error message is written to `stderr`.

When running a command with the -`h` or --`help` flag, the help is displayed and the process exits with code 2 to prevent unexpected behavior when piping the command into another command.

## JSON Output

Most {{% variables/axway_cli_prod_name %}} commands support the `--json` flag. When set, the data as well as any errors are output as JSON. You can pipe the output from one command into a tool such as jq ([https://stedolan.github.io/jq)](https://stedolan.github.io/jq))  and extract a specific value.

```
axway config ls --json
```

```
axway auth ls --json
```

```
axway org view --json
```

## Example

The following is an example `Node.js` script that authenticates, adds a team to an org, and add a org user to the new team.

```javascript
const clientId = 'DOSA_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';
const secretFile = 'private_key.pem'; // path to pem file
const username = 'your@email.com';
const password = 'your password';

const { spawnSync } = require('child_process');

spawnSync('axway', [
    'auth',
    'login',
    '--client-id', clientId,
    '--secret-file', secretFile,
    '--username', username,
    '--password', password
]);

let result = spawnSync('axway', [ 'org', 'view', '--json' ]);
const org = JSON.parse(result.stdout);
console.log(`Current org: ${org.name} (${org.guid})`);

result = spawnSync('axway', [ 'team', 'add', org.guid, 'My New Team', '--json' ])
const { team } = JSON.parse(result.stdout);

spawnSync('axway', [
    'team', 'user', 'add',
    org.guid,
    team.guid,
    'some_org_user@domain.com',
    '--role', 'administrator',
    '--json'
]);
```
