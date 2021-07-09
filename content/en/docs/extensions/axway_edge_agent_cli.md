---
title: Axway Edge Agent CLI
linkTitle: Axway Edge Agent CLI
description: ADD A DESCRIPTION
weight: 10
date: 2021-07-09
---

The Axway Edge Agent CLI is used to configure the Amplify Edge Agent and collect and upload subscription usage data to the Amplify Platform.

## Prerequisites

The Edge Agent CLI requires {{% variables/axway_cli_prod_name %}} 2.0.0 or later.

## Installation

To install the Axway Edge Agent CLI, run the following command from the terminal:

```
axway pm install @axway/axway-edge-agent-cli
```

## Getting started

To get a list of the available Axway Edge Agent CLI commands, run the following.

```
axway edge-agent
```

## Usage

```
axway edge-agent <commands> [options]
```

## Commands

* `autoReport` - Generate and upload a usage report
* `certs, certification, ingestionCertification` - Generate certificates for Edge Agent data ingestion
* `generateEnvId` - Generates an environment id. The environment id should be used in the Edge Agent configuration as envId. The envId is required for validation when uploading a usage report.
* `query,` `report`, `getReport` - query and export a usage report

### autoReport

Edge Agent collects data continuously from your on-premises product, generates, and uploads usage reports to the Platform.

#### autoReport usage

```
axway edge-agent autoReport <clientId> <privateKey> <organizationId> <userId> [options]
```

#### autoReport arguments

* `--clientId` - clientId for authentication
* `--privateKey` - path to private key for authentication
* `--organizationId` - id of organization for which to upload usage
* `--userId` - id of user uploading usage

#### autoReport options

* `--configurationName [value]` - Name of report configuration for which to generate report. Mandatory when multiple report configurations are available.
* `--daysOffset [value]` - Number of days offset. 1 corresponds to yesterday's report. The default is 1.
* `--daysReported [value]` - Number of days for which to generate report. The default is 1.
* `--logLevel [value]` - Logging detail level. The default is info.
* `--outputDir [value]` - Path to use when saving is enabled. The folder should already exist. default current path.
* `--outputFileExtension [value]` - Extension of file reported to Amplify. Also used when saving to disk. default '.json'
* `--outputFilePrefix [value]` - Prefix of file name reported to Amplify. Also used when saving to disk. default 'usage_report_'
* `--reportRestEndpoint [value]` - Edge Agent report generation URL. default '[http://localhost:9222/report/api/v1/query](http://localhost:9222/report/api/v1/query)'
* `--retries [value]` - Number of attempts to upload a report, retrying on upload error. The default is 5.
* `--retryPause [value]` - Second to wait between upload attempts. The default is 60.
* `--save` - Add flag to save report to disk before uploading.
* `--timeout [value]` - Seconds for timeout of report upload. Counted after successfully connected to the upload endpoint. The default is 60.
* `--tokenUrl [value]` - URL to authentication service. default [https://login.axway.com/auth/realms/Broker/protocol/openid-connect/token](https://login.axway.com/auth/realms/Broker/protocol/openid-connect/token)

### certs, certificates, ingestionCertificates

Generates certificates for Edge Agent data ingestion.

#### certs, certificates, ingestionCertificates usage

```
axway edge-agent certificates [options]
```

#### certs, certificates, ingestionCertificates options

* `--caAlias [value]` - Alias by which to import the certificate authority in the agent truststore. The default is CA.
* `--caCert [value]` - Certificate Authority certificate path. The default is CA.crt.
* `--caKey [value]` - Certificate Authority private key path. The default is CA.key.
* `--caPass [value]` - Certificate Authority key password. This is required.
* `--caValidDays [value]` - Number of days for which the generated Certificate Authority will be valid. The default is 3650.
* `--city [value]` - City information for generated CA & keystore
* `--clientCert [value]` - Client certificate path. The default is client.crt.
* `--clientCertAlias [value]` - Alias by which to import the client certificate in the agent truststore. defaults to client
* `--clientCertSignRequest [value]` - Client certificate signing request path. The default is clientCertSignRequest.csr.
* `--clientCertValidDays [value]` - Number of days for which the generated client certificate will be valid. The default is 3650.
* `--clientKey [value]` - Client certificate private key path. The default is client.key.
* `--clientPass [value]` - Client key password. This is required.
* `--conf [value]` - Path to configuration file. Configuration should match dotenv file specifications. Environment variables take precedence over the file. Explicit arguments will be used as overrides if give. The default is .env.
* `--country [value]` - Country information for generated CA & keystore
* `--keyStore [value]` - Server keystore path. The default is keystore.jks.
* `--keyStoreKeyAlias [value]` - Alias by which to identify the keystore key in keystore. The default is agent.
* `--keyStoreKeyPass [value]` - Keystore key password. This is required unless skipKeyStoreKeyGeneration is enabled.
* `--keyStoreKeyValidDays [value]` - Number of days for which the generated keystore key will be valid. The default is 3650.
* `--keyStorePass [value]` - Keystore password. This is required unless skipKeyStoreKeyGeneration is enabled.
* `--logLevel [value]` - Logging detail level. The default is info.
* `--org [value]` - Organization information for generated CA & keystore
* `--orgUnit [value]` - Organization unit information for generated CA & keystore
* `--overwriteCa` - Overwrite the Certificate Authority certificate and key if they already exist
* `--overwriteClientCert` - Overwrite the client certificate and key if they already exist
* `--skipCaGeneration` - Use an existing certificate authority instead of generating a new one
* `--skipCaImport` - Do not import the certificate authority in the server truststore
* `--skipClientGeneration` - Do not generate a client certificate and key
* `--skipKeyStoreKeyGeneration` - Do not generate a new keystore key
* `--state [value]` - State information for generated CA & keystore
* `--trustStore [value]` - Server truststore path. defaults to truststore.jks
* `--trustStorePass [value]` - Truststore password. Required

### generateEnvId

Generates an environment id that is used in the Edge Agent configuration as `envId`. The `envId` is required for validation when uploading a usage report.

#### generateEnvId usage

```
axway edge-agent generateEnvId
```

#### generateEnvId options

* `--envIdFile [value]` - Define a new name for the output file. The default is envId.txt.
* `--logLevel [value]` - Logging detail level. The default is info.
* `--outputDir [value]`\- Parent folder for the output file. It folder should already exist before calling the command. The default is the current directory.

### query, report, getReport

Queries and exports a usage report.

#### query, report, getReport usage

```
axway edge-agent query <from> [options] [<to>]
```

#### query, report, getReport arguments

* `from` - the start time for the report
* `to` - the end time of the report. The default is now.

#### query, report, getReport options

* `--configurationName [value]` - Name of report configuration for which to generate report. Mandatory when multiple report configurations are available
* `--logLevel [value]` - Logging detail level. The default is info.
* `--outputDir [value]` - Path to use when saving is enabled. The folder should already exist. The default is the current path.
* `--outputFileExtension [value]` - Extension of output file. default '.json'
* `--outputFilePrefix [value]` - Prefix of output file name. default 'usage_report_'
* `--reportRestEndpoint [value]` - Edge Agent report generation URL. The default is '[http://localhost:9222/report/api/v1/query](http://localhost:9222/report/api/v1/query)'.
* `--unwrapJsonContent [value]` - Extract report content from the json response body. The default is true.
