---
name: Salesforce
stage: GA
title: Salesforce Source Plugin
description: CloudQuery Salesforce source plugin documentation
---

# Salesforce Source Plugin

:badge

The CloudQuery Salesforce plugin extracts information from your Salesforce organization(s) and loads it into any supported CloudQuery destination (e.g. PostgreSQL, BigQuery, Snowflake, and [more](/docs/plugins/destinations/overview)).

## Authentication

:authentication

## Configuration

This example syncs from Salesforce to a Postgres destination:

:configuration

:::callout{type="info"}
Make sure you use environment variable expansion in production instead of committing the credentials to the configuration file directly.
:::callout{type="info"}

## Salesforce Spec

This is the (nested) spec used by the Slack source plugin.

- `client_id` (string, required):

  This is the consumer key of the connected app. This can be obtained by [Creating a Salesforce connected app](/docs/plugins/sources/salesforce/creating_connected_app).

- `client_secret` (string, required):

  This is the consumer secreted of the connected app. This can be obtained by [Creating a Salesforce connected app](/docs/plugins/sources/salesforce/creating_connected_app).

- `username` (string, required):

  This is the username of the Salesforce user that will be used to authenticate with Salesforce. This user must have the permissions to access the Salesforce objects you want to sync. It is best to limit the permission of this user to read only.

- `password` (string, required):

  This is the password of the above Salesforce user.

- `include_objects` (string array, optional):

  By default the plugin will sync all Salesforce objects. If you want to limit the objects that are synced you can specify the objects you want to sync in this array.

- `exclude_objects` (string array, optional):

  By default the plugin will sync all Salesforce objects. If you want to exclude some objects from being synced you can specify the objects you want to exclude in this array.

- `concurrency` (int, optional, default: 10000):
  A best effort maximum number of Go routines to use. Lower this number to reduce memory usage.

## Example Queries

### List all Salesforce objects

```sql copy
select distinct(object_type) from salesforce_objects;
```

### List all Accounts

```sql copy
select * from salesforce_objects where object_type = 'Account';
```
