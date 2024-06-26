---
name: OracleDB
title: OracleDB Source Plugin
description: CloudQuery OracleDB source plugin documentation
---

# OracleDB Source Plugin

:badge

The CloudQuery OracleDB plugin syncs your OracleDB database to any of the supported CloudQuery destinations (e.g. PostgreSQL, BigQuery, Snowflake, and [more](/docs/plugins/destinations/overview)).
Supported database versions are >= 18c (see more about database release schedule [here](https://support.oracle.com/knowledge/Oracle%20Database%20Products/742060_1.html)).

### Example

This example configures a OracleDB source, located at `localhost:1521`. The (top level) spec section is described in the [Source Spec Reference](/docs/reference/source-spec).

:configuration

## OracleDB spec

This is the (nested) spec used by the OracleDB destination plugin.

- `connection_string` (string, required)

  Connection string to connect to the database in the format `oracle://<user<>:<password>@<server>:<port>/<service_name>`. To use the default `1521` port, you can omit it from the connection string, but still need to keep the `:`, for example `oracle://<user<>:<password>@<server>:/<service_name>`.
  See the [Go driver documentation](https://github.com/sijms/go-ora) for more details.

- `concurrency` (int, optional, default: 100):
  Number of tables to sync concurrently. Lower or increase this number based on your database size and available resources.

:::callout{type="info"}
Make sure you use [environment variable expansion](/docs/advanced-topics/environment-variable-substitution) in production instead of committing the credentials to the configuration file directly.
:::
