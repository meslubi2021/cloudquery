---
name: DuckDB
stage: GA
title: DuckDB Destination Plugin
description: CloudQuery DuckDB destination plugin documentation
---
# DuckDB Destination Plugin

:badge

This destination plugin lets you sync data from a CloudQuery source to a [DuckDB](https://duckdb.org/) database.

## Example Config

:configuration

## DuckDB Spec

This is the top level spec used by the DuckDB destination Plugin.

- `connection_string` (`string`) (required)

  Absolute or relative path to a file, such as `./example.duckdb`.

- `batch_size` (`integer`) (optional) (default: `1000`)

  This parameter controls the maximum amount of items may be grouped together to be written as a single write.

- `batch_size_bytes` (`integer`) (optional) (default: `4194304` (4 MiB))

  This parameter controls the maximum size of items that may be grouped together to be written as a single write.

- `debug` (`boolean`) (optional) (default: `false`)

  Allows to enable debug logging.
