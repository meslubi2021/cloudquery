# Table: googleads_ad_group_labels

This table shows data for Google Ads Ad Group Labels.

https://developers.google.com/google-ads/api/reference/rpc/v13/AdGroupLabel

The composite primary key for this table is (**customer_id**, **resource_name**, **ad_group**).

## Relations

This table depends on [googleads_ad_groups](googleads_ad_groups).

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|customer_id (PK)|`int64`|
|resource_name (PK)|`utf8`|
|ad_group (PK)|`utf8`|
|label|`utf8`|