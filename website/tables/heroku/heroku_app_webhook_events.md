# Table: heroku_app_webhook_events

This table shows data for Heroku App Webhook Events.

https://devcenter.heroku.com/articles/platform-api-reference#app-webhook-event

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|created_at|`timestamp[us, tz=UTC]`|
|include|`utf8`|
|payload|`json`|
|updated_at|`timestamp[us, tz=UTC]`|