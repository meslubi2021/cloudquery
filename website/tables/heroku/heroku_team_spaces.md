# Table: heroku_team_spaces

This table shows data for Heroku Team Spaces.

https://devcenter.heroku.com/articles/platform-api-reference#team-space

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|cidr|`utf8`|
|created_at|`timestamp[us, tz=UTC]`|
|data_cidr|`utf8`|
|name|`utf8`|
|organization|`json`|
|region|`json`|
|shield|`bool`|
|state|`utf8`|
|team|`json`|
|updated_at|`timestamp[us, tz=UTC]`|