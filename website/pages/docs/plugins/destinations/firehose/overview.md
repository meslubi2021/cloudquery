---
name: Amazon Kinesis Firehose
title: Amazon Kinesis Firehose Destination Plugin
description: CloudQuery Amazon Kinesis Firehose destination plugin documentation
---

# Amazon Kinesis Firehose Destination Plugin

:badge

This destination plugin lets you sync data from a CloudQuery source to Amazon Kinesis Firehose.

## Authentication

:authentication

## Example

:configuration

The (top level) spec section is described in the [Destination Spec Reference](/docs/reference/destination-spec).

The Amazon Kinesis Firehose destination utilizes batching, and supports [`batch_size`](/docs/reference/destination-spec#batch_size) and [`batch_size_bytes`](/docs/reference/destination-spec#batch_size_bytes). 

It is important to note that Amazon Kinesis Firehose has the following limitations that cannot be changed:
  - The maximum size of a record sent to Kinesis Data Firehose, before base64-encoding, is 1,000 KiB.
  - The `PutRecordBatch` operation can take up to 500 records per batch or 4 MiB per batch, whichever is smaller.

## Firehose Spec

- `stream_arn` (`string`) (required)

  Kinesis Firehose delivery stream where data will be sent.

- `max_retries` (`integer`) (optional) (default: `5`)

  Amount of retries to perform when writing a batch.

- `max_record_size_bytes` (`integer`) (optional) (default: `1024000` (1000 KiB))

  Number of bytes (as Arrow buffer size) to write before starting a new record.

- `max_batch_records` (`integer`) (optional) (default: `500` (1000 KiB))

  Number of records allowed in a single batch.

- `max_batch_size_bytes` (`integer`) (optional) (default: `4194000` (~4000 KiB))

  Number of bytes allowed in a single batch.
