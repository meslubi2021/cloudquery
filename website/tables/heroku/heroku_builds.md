# Table: heroku_builds

This table shows data for Heroku Builds.

https://devcenter.heroku.com/articles/platform-api-reference#build

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|app|`json`|
|buildpacks|`json`|
|created_at|`timestamp[us, tz=UTC]`|
|output_stream_url|`utf8`|
|release|`json`|
|slug|`json`|
|source_blob|`json`|
|stack|`utf8`|
|status|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|
|user|`json`|