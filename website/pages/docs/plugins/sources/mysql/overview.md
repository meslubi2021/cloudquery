---
name: MySQL
title: MySQL Source Plugin
description: CloudQuery MySQL source plugin documentation
---
# MySQL Source Plugin

:badge

The CloudQuery MySQL plugin syncs your MySQL database to any of the supported CloudQuery destinations (e.g. PostgreSQL, BigQuery, Snowflake, and [more](/docs/plugins/destinations/overview)).
Supported database versions are >= 5.7.

### Example

This example configures a MySQL source, located at `localhost:3306`. The (top level) spec section is described in the [Source Spec Reference](/docs/reference/source-spec).

:configuration

## MySQL spec

This is the (nested) spec used by the MySQL destination plugin.

- `connection_string` (string, required)

  Connection string to connect to the database. See the [Go driver documentation](https://github.com/go-sql-driver/mysql#dsn-data-source-name) for more details.

:::callout{type="info"}
Make sure you use [environment variable expansion](/docs/advanced-topics/environment-variable-substitution) in production instead of committing the credentials to the configuration file directly.
:::
