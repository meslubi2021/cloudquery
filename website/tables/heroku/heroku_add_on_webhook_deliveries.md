# Table: heroku_add_on_webhook_deliveries

This table shows data for Heroku Add On Webhook Deliveries.

https://devcenter.heroku.com/articles/platform-api-reference#add-on-webhook-delivery

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|created_at|`timestamp[us, tz=UTC]`|
|event|`json`|
|last_attempt|`json`|
|next_attempt_at|`timestamp[us, tz=UTC]`|
|num_attempts|`int64`|
|status|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|
|webhook|`json`|