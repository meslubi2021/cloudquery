# Table: render_service_jobs

This table shows data for Render Service Jobs.

The primary key for this table is **id**.

## Relations

This table depends on [render_services](render_services).

## Columns

| Name          | Type          |
| ------------- | ------------- |
|service_id|`utf8`|
|id (PK)|`utf8`|
|name|`utf8`|
|domain_type|`utf8`|
|public_suffix|`utf8`|
|redirect_for_name|`utf8`|
|created_at|`timestamp[us, tz=UTC]`|
|server|`json`|