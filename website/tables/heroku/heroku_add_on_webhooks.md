# Table: heroku_add_on_webhooks

This table shows data for Heroku Add On Webhooks.

https://devcenter.heroku.com/articles/platform-api-reference#add-on-webhook

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|created_at|`timestamp[us, tz=UTC]`|
|include|`list<item: utf8, nullable>`|
|level|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|
|url|`utf8`|