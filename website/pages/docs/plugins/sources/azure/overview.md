---
name: Azure
stage: GA
title: Azure Source Plugin
description: CloudQuery Azure Plugin documentation
---
# Azure Source Plugin

:badge

The CloudQuery Azure source plugin extracts information from many of the supported services by Microsoft Azure and loads it into any supported CloudQuery destination (e.g. PostgreSQL, BigQuery, Snowflake, and [more](/docs/plugins/destinations/overview)).

## Authentication

:authentication

For best performance we recommend creating a service principal and using environment variables to authenticate.
For testing purposes only you can use [`az login`](#authentication-with-az-login) to authenticate.

### Authentication with Environment Variables

You will need to create a service principal for the plugin to use:

#### Creating a service principal

First, install the Azure CLI (`az`).

Then, login with the Azure CLI:

```bash copy
az login
```

Then, create the service principal the plugin will use to access your cloud deployment. WARNING: The output of
`az ad sp create-for-rbac` contains credentials that you must protect - Make sure to handle with appropriate care.
This example uses bash - The commands for CMD and PowerShell are similar.

```bash copy
export SUBSCRIPTION_ID=<YOUR_SUBSCRIPTION_ID>
az account set --subscription $SUBSCRIPTION_ID
az provider register --namespace 'Microsoft.Security'

# Create a service-principal for the plugin
az ad sp create-for-rbac --name cloudquery-sp --scopes /subscriptions/$SUBSCRIPTION_ID --role Reader
```

(you can, of course, choose any name you'd like for your service-principal, `cloudquery-sp` is just an example.
If the service principal doesn't exist it will create a new one, otherwise it will update an existing one)

The output of `az ad sp create-for-rbac` should look like this:

```json copy
{
  "appId": "YOUR AZURE_CLIENT_ID",
  "displayName": "cloudquery-sp",
  "password": "YOUR AZURE_CLIENT_SECRET",
  "tenant": "YOUR AZURE_TENANT_ID"
}
```

#### Exporting environment variables

Next, you need to export the environment variables that plugin will use to sync your cloud configuration.
Copy them from the output of `az ad sp create-for-rbac` (or, take the opportunity to show off your jq-foo).
The example shows how to export environment variables for Linux - exporting for CMD and PowerShell is similar.

- `AZURE_TENANT_ID` is `tenant` in the JSON.
- `AZURE_CLIENT_ID` is `appId` in the JSON.
- `AZURE_CLIENT_SECRET` is `password` in the JSON.

```bash copy
export AZURE_TENANT_ID=<YOUR AZURE_TENANT_ID>
export AZURE_CLIENT_ID=<YOUR AZURE_CLIENT_ID>
export AZURE_CLIENT_SECRET=<YOUR AZURE_CLIENT_SECRET>
export AZURE_SUBSCRIPTION_ID=$SUBSCRIPTION_ID
```

### Authentication with `az login`

First, install the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) (`az`). Then, login with the Azure CLI:

```bash copy
az login
```

You are now authenticated!

:::callout{type="info"}
Using only `az login` is not recommended for production use, as it requires spawning a new Azure CLI process each time an authentication token is needed.
:::

## Query Examples

### Find all MySQL servers

```sql copy
SELECT * FROM azure_mysql_servers;
```

### Find storage accounts that are allowing non-HTTPS traffic

```sql copy
SELECT * from azure_storage_accounts where enable_https_traffic_only = false;
```

### Find all expired key vaults

```sql copy
SELECT * from azure_keyvault_vault_keys where attributes_expires >= extract(epoch from now()) * 1000;
```

### List the Memory and vCPUs of all available Azure Compute VM types

```sql copy
SELECT
 distinct(vm.name),
 vcpus.capability_value AS "vCPUs",
 memory.capability_value AS "Memory"
FROM
 azure_compute_skus vm
 CROSS JOIN LATERAL (
   SELECT (caps ->> 'value') AS capability_value
   FROM jsonb_array_elements(vm.capabilities) caps
   WHERE (caps ->> 'name') = 'vCPUs'
 ) vcpus
 CROSS JOIN LATERAL (
   SELECT (caps ->> 'value') AS capability_value
   FROM jsonb_array_elements(vm.capabilities) caps
   WHERE (caps ->> 'name') = 'MemoryGB'
 ) memory
WHERE
 vm.resource_type = 'virtualMachines' order by name;
```

Results:

```bash
+---------------------------+-------+--------+
| name                      | vCPUs | Memory |
|---------------------------+-------+--------|
| Basic_A0                  | 1     | 0.75   |
| Basic_A1                  | 1     | 1.75   |
| Basic_A2                  | 2     | 3.5    |
| Basic_A3                  | 4     | 7      |
| Basic_A4                  | 8     | 14     |
| Standard_A0               | 1     | 0.75   |
| Standard_A1               | 1     | 1.75   |
| Standard_A1_v2            | 1     | 2      |
... (truncated)
```
