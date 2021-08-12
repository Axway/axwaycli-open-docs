---
title: Troubleshooting
linkTitle: Troubleshooting
description: Troubleshoot errors and other messages you may receive using the Axway CLI. Learn why the message may have occurred and suggested methods to resolve the issue.
weight: 70
date: 2021-07-09
---

## Authentication issues

This section includes troubleshooting for authentication issues.

### Error: Amplify Auth requires "libsecret" which must be manually installed.

The {{% variables/axway_cli_prod_name %}} by default will store your access tokens securely in a file on disk. On Linux, we use a library that requires `libsecret`. To install it, run:

```bash
# Debian/Ubuntu:
sudo apt-get install libsecret-1-dev

# Red Hat-based:
sudo yum install libsecret-devel

# Arch Linux:
sudo pacman -S libsecret
```

### Error: Authentication failed: 400 invalid_grant: Session not active

This is caused by a bug and occurs when your access token has expired, but your refresh token is still valid. The {{% variables/axway_cli_prod_name %}} will attempt to get a new access token using the refresh token, but the server has revoked your tokens and you must re-authenticate.

The workaround is to log out and log back in:

```
axway auth logout
axway auth login
```

### Error: Cannot autolaunch D-Bus without X11 $DISPLAY

This issue occurs on headless Linux machines, Docker containers, and SSH sessions. The problem is the `libsecret` library has dependencies on X11 display server so that a dialog can prompt the user for their password and unlock the secure token store encryption key.

Unfortunately, headless Linux environments are not supported.

### Error: Failed to install keytar@<version>

This error occurs when running an auth related command. The  `keytar`  library is likely corrupt or incomplete. You can manually delete the  `keytar` files and rerun the auth command.

The `keytar` files are located at:

```
C:\Users\<username>\.axway\axway-cli\lib\keytar
```

### Error: Fetch user info failed: Response code 401 (Unauthorized)

This is caused by a bug and occurs when you think you have a valid access token, but the {{% variables/axway_cli_prod_name %}} has revoked the access token. This is most likely caused by switching your current selected organization.

The workaround is to log out and log back in:

```
axway auth logout
axway auth login
```

### Error: Prebuild-install WARN install self signed certificate in certificate chain (code 1)

This issue is caused when the {{% variables/axway_cli_prod_name %}} attempts to install the `keytar` library and you are using a proxy server that uses a self-signed certificate. By default, Node.js (and npm) error when making an HTTPS request to a server that has a TLS certificate that is signed by an unknown authority. There are two workarounds.

1\. Disable secure token storage:

```
axway config set auth.tokenStoreType file
```

or

2\. Disable Node.js TLS certificate validation by setting the following environment variable:

```
# Linux/macOS
export NODE_TLS_REJECT_UNAUTHORIZED=0

# Windows
set NODE_TLS_REJECT_UNAUTHORIZED 0
```

### Error: /lib64/libstdc++.so.6: version \`GLIBCXX_3.4.21' not found

This issue is caused by the {{% variables/axway_cli_prod_name %}} attempting to use the `keytar` library needed to securely store your access tokens and only occurs on Linux machines. There are two workarounds:

1\. Install the required library. Please refer to your Linux distribution’s documentation and package manager for how to install the correct version of this required library.

Or

2. Disable the secure token store:

```
axway config set auth.tokenStoreType file
```

### Login hangs or Error: Failed to open web browser

By default, the {{% variables/axway_cli_prod_name %}} authenticates using your web browser. The {{% variables/axway_cli_prod_name %}} will appear to freeze or hang while it waits for the browser to open and for you to sign in. The {{% variables/axway_cli_prod_name %}} does not know if the browser launched successfully and thus it appears it has hung.

Try the following:

1. Logout by running `axway auth logout --all`, then login again
2. Restart your terminal to ensure the system paths are untainted and that the {{% variables/axway_cli_prod_name %}} can find your default web browser, then login again
3. Disable launching the browser and manually copy and paste the URL into your browser by running `axway auth login --no-launch-browser`

Note that your web browser must be in the same environment for which the login command was run. You cannot authenticate a remote or headless machine unless you have been issued by Axway ID a signed JWT token or client secret service account.

### node: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

This issue is caused by the {{% variables/axway_cli_prod_name %}} attempting to use the `keytar` library needed to securely store your access tokens and only occurs on Linux machines. There are two workarounds:

1\. Install the required library. Please refer to your Linux distribution’s documentation and package manager for how to install the correct version of this required library.

Or

2. Disable the secure token store:

```
axway config set auth.tokenStoreType file
```

### Secure token store is not available

This issue can occur in {{% variables/axway_cli_prod_name %}} 1.1.0 and older on Linux and macOS. It's caused by a failure to install the `keytar` library needed to securely store your access tokens.

The most likely culprit is a permission issue accessing the npm home directory `~/.npm` when compiling `keytar`. You can try to manually fix the file permissions or re-install the {{% variables/axway_cli_prod_name %}} with unsafe permissions disabled:

```bash
npm i -g --unsafe-perm axway
```

## Installation issues

This section includes troubleshooting for installation issues.

### Error: EACCESS: permission denied, access '/usr/local/lib/node_modules'

When installing the {{% variables/axway_cli_prod_name %}} on macOS or Linux, the global install location may require elevated access permissions.

One solution is to rerun the install using sudo:

```bash
sudo npm i -g axway
```

Another option is to change the file owner of the global install location:

```bash
sudo chown -R $(whoami) /usr/local/bin /usr/local/lib/node_modules
```

`npm` offers two more options: use a node version manager or change `npm`'s default directory. Visit `npm`'s documentation for more details: [https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally).

### Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/axway/node_modules/keytar/.node-gyp'

When installing the {{% variables/axway_cli_prod_name %}} on a macOS or Linux machine, npm may run into permission issues installing the {{% variables/axway_cli_prod_name %}} globally. There are three workarounds:

1. Specify the --unsafe-perm flag to signal `npm` to run the keytar installer as your sudo user:{{}}

    ```bash
    sudo npm install -g axway --unsafe-perm
    ```

2. Change the file permissions of the global `npm` install path:

    ```bash
    sudo chmod -R $(whoami) /usr/local/bin /usr/local/lib/node_modules

    npm install -g axway
    ```

3. Change the `npm` global install path to your home directory:

    ```bash
    mkdir -p ~/.npm-global

    npm config set prefix "~/.npm-global"

    export PATH=~/.npm-global/bin:$PATH

    source ~/.profile # Linux
    source ~/.bashrc # macOS

    npm install -g axway
    ```

### npm ERR! Code EEXISTS

When installing the {{% variables/axway_cli_prod_name %}} on Windows machines, npm may encounter a file locking issue. The easiest solution is to reinstall the {{% variables/axway_cli_prod_name %}} using the `--force` flag.

```bash
npm i -g --force axway
```

### npm ERR! Code ENOENT

When installing the {{% variables/axway_cli_prod_name %}} on Windows machines, npm may encounter a file locking issue. The easiest solution is to reinstall the {{% variables/axway_cli_prod_name %}} using the `--force` flag.

```bash
npm i -g --force axway
```

This error can also occur on Windows machines when executing an auth related command. This is likely due to the {{% variables/axway_cli_prod_name %}} installing the  `keytar` library needed to securely store your access tokens. Assuming the  `keytar`  install has become corrupt, you can manually delete the  `keytar` files and rerun the auth command.

The `keytar` files are located at:

```
C:\Users\<username>\.axway\axway-cli\lib\keytar
```

### prebuild-install WARN install EACCES: permission denied, access '/home/<user>/.npm'

When installing the {{% variables/axway_cli_prod_name %}} on a macOS or Linux machine, npm may run into permission issues installing the {{% variables/axway_cli_prod_name %}} globally. There are three workarounds:

1. Specify the --unsafe-perm flag to signal `npm` to run the keytar installer as your sudo user:{{}}

    ```bash
    sudo npm install -g axway --unsafe-perm
    ```

2. Change the file permissions of the global `npm` install path:

    ```bash
    sudo chmod -R $(whoami) /usr/local/bin /usr/local/lib/node_modules

    npm install -g axway
    ```

3. Change the `npm` global install path to your home directory:

    ```bash
    mkdir -p ~/.npm-global

    npm config set prefix "~/.npm-global"

    export PATH=~/.npm-global/bin:$PATH

    source ~/.profile # Linux
    source ~/.bashrc # macOS

    npm install -g axway
    ```

## Network issues

This section includes troubleshooting for network issues.

### Error: tunneling socket could not be established, cause=self signed certificate

This occurs when you are using a proxy server with a self signed SSL certificate. The only way to get around this is to disable Node.js TLS certificate validation by setting the following environment variable:

```
# Linux/macOS
export NODE_TLS_REJECT_UNAUTHORIZED=0

# Windows
set NODE_TLS_REJECT_UNAUTHORIZED 0
```

### RequestError: self signed certificate

This occurs when you are using a proxy server with a self signed SSL certificate. The only way to get around this is to disable Node.js TLS certificate validation by setting the following environment variable:

```
# Linux/macOS
export NODE_TLS_REJECT_UNAUTHORIZED=0

# Windows
set NODE_TLS_REJECT_UNAUTHORIZED 0
```

## Package manager issues

This section includes troubleshooting for package manager issues.

### Error: Failed to npm install <package> (code 243)

This is likely an "EACCES" error that affects macOS and Linux users in which npm cannot write to its cache directory due to a file permission issue.

To fix the file owner to your current user, run:

```bash
sudo chown -R $(id -u):$(id -g) ~/.npm
```
