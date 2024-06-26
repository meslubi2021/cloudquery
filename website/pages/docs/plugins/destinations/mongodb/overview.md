---
name: MongoDB
stage: GA
title: MongoDB Destination Plugin
description: CloudQuery MongoDB destination plugin documentation
---
# MongoDB Destination Plugin

:badge

This destination plugin lets you sync data from any CloudQuery source to a MongoDB database.

Supported database versions:

- MongoDB >= 3.6 (The same minimum version supported by the official [Go driver](https://github.com/mongodb/mongo-go-driver))

## Configuration

### Example

:configuration

:::callout{type="info"}
Make sure to use [environment variable substitution](/docs/advanced-topics/environment-variable-substitution) in production instead of committing the credentials to the configuration file directly.
:::

The MongoDB destination utilizes batching, and supports [`batch_size`](/docs/reference/destination-spec#batch_size) and [`batch_size_bytes`](/docs/reference/destination-spec#batch_size_bytes). 

### MongoDB Spec

This is the (nested) spec used by the MongoDB destination Plugin.

- `connection_string` (`string`) (required)

  MongoDB URI as described in the official MongoDB [documentation](https://www.mongodb.com/docs/manual/reference/connection-string/).

- `database` (`string`) (required)

  Required database to sync the data to.

- `batch_size` (`integer`) (optional) (default: `1000`)

  This parameter controls the maximum amount of items may be grouped together to be written as a single write.

- `batch_size_bytes` (`integer`) (optional) (default: `4194304` (= 4 MiB))

  This parameter controls the maximum size of items that may be grouped together to be written as a single write.
