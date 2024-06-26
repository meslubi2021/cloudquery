---
name: GCS
stage: GA
title: GCS Destination Plugin
description: CloudQuery GCS destination plugin documentation
---
# GCS (Google Cloud Storage) Destination Plugin

:badge

This destination plugin lets you sync data from a CloudQuery source to remote GCS (Google Cloud Storage) storage in various formats such as CSV, JSON and Parquet.

This is useful in various use-cases, especially in data lakes where you can query the data direct from Athena or load it to various data warehouses such as BigQuery, RedShift, Snowflake and others.

## Example

:configuration

The GCS destination utilizes batching, and supports `batch_size`, `batch_size_bytes` and `batch_timeout` options (see below).

## GCS Spec

This is the (nested) spec used by the CSV destination Plugin.

- `bucket` (`string`) (required)

  Bucket where to sync the files.

- `path` (`string`) (required)

  Path to where the files will be uploaded in the above bucket.

- `format` (`string`) (required)

  Format of the output file. Supported values are `csv`, `json` and `parquet`.

- `format_spec` ([format_spec](#format_spec)) (optional)

  Optional parameters to change the format of the file.

- `compression` (`string`) (optional) (default: empty)

  Compression algorithm to use. Supported values are empty or `gzip`. Not supported for `parquet` format.

- `no_rotate` (`boolean`) (optional) (default: `false`)

  If set to `true`, the plugin will write to one file per table.
  Otherwise, for every batch a new file will be created with a different `.<UUID>` suffix.

- `batch_size` (`integer`) (optional) (default: `10000`)

  Number of records to write before starting a new object.

- `batch_size_bytes` (`integer`) (optional) (default: `52428800` (50 MiB))

  Number of bytes (as Arrow buffer size) to write before starting a new object.

- `batch_timeout` (`duration`) (optional) (default: `30s` (30 seconds))

  Inactivity time before starting a new object.

### format_spec

- `delimiter` (`string`) (optional) (default: `,`)

  Character that will be used as want to use as the delimiter if the format type is `csv`.

- `skip_header` (`boolean`) (optional) (default: `false`)

  Specifies if the first line of a file should be the headers (when format is `csv`).

## Authentication

:authentication