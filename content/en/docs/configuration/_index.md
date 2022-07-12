---
title: Configuration
linkTitle: Configuration 
weight: 30
date: 2021-07-09
---

Use the Axway CLI config command to manage configuration values.

## Settings

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `auth.serverHost` | string | <span style="white-space:nowrap">`"localhost"`</span> | The hostname the local web server should listen on and await the successful login browser redirect. |
| `auth.serverPort` | number | `3000` | The port number the local web server should listen on and await the successful login browser redirect. The value must be between `1024` and `65535`. |
| <span style="white-space:nowrap">`auth.tokenRefreshThreshold`</span> | number | `900` | The number of seconds before a service account's access token expires when it should be refreshed. This setting only applies when the `auth.tokenStoreType` is set to `"secure"` (the default value). The value must be a non-negative integer. Defaults to 15 minutes. |
| `auth.tokenStoreType` | string | `"secure"` | After authenticating, access tokens are encrypted and stored in a file called the token store. Access to this file is restricted to only the owner (the current user). By default, the encryption key is stored in the system's keychain, however this feature is unavailable in headless environments such as SSH terminals and this setting must be set to `file`.<br /><br />Allowed values:<br /><br />**auto** - Attempts to use the **secure** store, but falls back to **file** if secure store is unavailable.<br /><br />**secure** - Encrypts the access token using a generated key which is stored in the system's keychain.<br /><br />**file** - Encrypts the access token using the embedded key.<br /><br />**memory** - Stores the access token in memory instead of on disk. The access tokens are lost when the process exits. This is intended for testing purposes only.<br /><br />**null** - Disables all forms of token persistence and only returns the access token. Subsequent calls to login in the same process will force the authentication flow. This is intended for migration scripts and testing purposes only. |
| `network.caFile` | string |  | The path to a PEM formatted certificate authority bundle used to validate untrusted SSL certificates. |
| `network.proxy` | string |  | The proxy server URL. This proxy server is used for both HTTP and HTTPS requests.<br /><br />{{% alert title="Note" color="primary" %}}If the proxy server uses a self-signed certificate, you must specify the `network.caFile`, set `network.strictSSL` to `false`, or set the environment variable `NODE_TLS_REJECT_UNAUTHORIZED=0`.{{% /alert %}} |
| `network.strictSSL` | boolean | `true` | Enforces valid TLS certificates on all outbound HTTPS requests. Set this to `false` if you are behind a proxy server with a self-signed certificate. |

## Usage

``` bash
axway config [--json] <action> [<key>] [<value>]
```

## Commands

* `get` - Display a specific config setting
* `ls`, `list` - Display all config settings
* `pop` - Remove the last value in a list
* `push` - Add a value to the end of a list
* `rm`, `delete` - Remove a config setting
* `set` - Change a config setting
* `shift` - Remove the first value in a list
* `unshift` - Add a value to the beginning of a list

### Options

* `--json` - Output the value as JSON

### get

Returns a config setting.

``` bash
axway config get <key>
```

### ls, list

Displays a list of all installed packages.

``` bash
axway config ls
```

``` bash
axway config list
```

### pop

Removes a value from the end of a list.

``` bash
axway config pop <key>
```

### push

Adds a value to the end of a list. If there is no existing value, a new list is created. If a non-list value exists, it is converted to a list and the new value is appended.

``` bash
axway config pop <key> <value>
```

### rm, delete

Deletes a config setting.

``` bash
axway config rm <key>
```

``` bash
axway config delete <key>
```

### set

Sets a config value. If a value already exists, the existing value is overwritten.

``` bash
axway config set <key> <value>
```

### shift

Removes a value from the beginning of a list.

``` bash
axway config shift <key>
```

### unshift

Adds a value to the beginning of a list. If there is no existing value, a new list is created. If a non-list value exists, it is converted to a list and the new value is prepended.

``` bash
axway config unshift <key> <value>
```
