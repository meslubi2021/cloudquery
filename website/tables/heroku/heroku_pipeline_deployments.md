# Table: heroku_pipeline_deployments

This table shows data for Heroku Pipeline Deployments.

https://devcenter.heroku.com/articles/platform-api-reference#pipeline-deployment

The primary key for this table is **id**.

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|id (PK)|`utf8`|
|addon_plan_names|`list<item: utf8, nullable>`|
|app|`json`|
|created_at|`timestamp[us, tz=UTC]`|
|current|`bool`|
|description|`utf8`|
|output_stream_url|`utf8`|
|slug|`json`|
|status|`utf8`|
|updated_at|`timestamp[us, tz=UTC]`|
|user|`json`|
|version|`int64`|