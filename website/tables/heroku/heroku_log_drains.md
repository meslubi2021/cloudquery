# Table: heroku_log_drains

This table shows data for Heroku Log Drains.

https://devcenter.heroku.com/articles/platform-api-reference#log-drain

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|addon|`json`|
|created_at|`timestamp[us, tz=UTC]`|
|token|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|
|url|`utf8`|