---
name: Azure DevOps
stage: GA
title: Azure DevOps Source Plugin
description: CloudQuery Azure DevOps Plugin documentation
---

# Azure DevOps Source Plugin

:badge

The CloudQuery Azure DevOps plugin reads information from your Azure DevOps account and loads it into any supported CloudQuery destination (e.g. PostgreSQL, Snowflake, BigQuery, and [more](/docs/plugins/destinations/overview)).

## Configuration

This example syncs from Azure DevOps to a destination. The (top level) source spec section is described in the [Source Spec Reference](/docs/reference/source-spec).

:configuration

For more information on downloading, installing and running the CloudQuery CLI, see the [Quickstart guide](/docs/quickstart).

## Authentication

:authentication

## Azure DevOps Spec

This is the (nested) spec used by the Azure DevOps source plugin.

- `concurrency` (`int`) (default: `10000`):

  A best effort maximum number of Go routines to use. Lower this number to reduce memory usage.

- `personal_access_token` (`string`, required):

  An API token to access Azure DevOps resources. This can be obtained by [creating an API token](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows#create-a-pat). It's recommended to allow only read access to the resources you need to sync.

- `organization_url` (`[]string`, required):

  The Azure DevOps organization URL. Should be in the format `https://dev.azure.com/{organization}`.
