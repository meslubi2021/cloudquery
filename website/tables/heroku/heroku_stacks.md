# Table: heroku_stacks

This table shows data for Heroku Stacks.

https://devcenter.heroku.com/articles/platform-api-reference#stack

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|created_at|`timestamp[us, tz=UTC]`|
|default|`bool`|
|name|`utf8`|
|state|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|