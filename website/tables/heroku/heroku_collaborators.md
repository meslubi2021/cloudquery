# Table: heroku_collaborators

This table shows data for Heroku Collaborators.

https://devcenter.heroku.com/articles/platform-api-reference#collaborator

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|app|`json`|
|created_at|`timestamp[us, tz=UTC]`|
|permissions|`json`|
|role|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|
|user|`json`|