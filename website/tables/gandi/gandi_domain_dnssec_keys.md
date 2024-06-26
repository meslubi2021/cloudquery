# Table: gandi_domain_dnssec_keys

This table shows data for Gandi Domain DNSSEC Keys.

The composite primary key for this table is (**fqdn**, **id**).

## Relations

This table depends on [gandi_domains](gandi_domains).

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|fqdn (PK)|`utf8`|
|id (PK)|`int64`|
|algorithm|`int64`|
|digest|`utf8`|
|digest_type|`int64`|
|keytag|`int64`|
|type|`utf8`|
|public_key|`utf8`|