# Table: slack_conversation_histories

This table shows data for Slack Conversation Histories.

https://api.slack.com/methods/conversations.history

The composite primary key for this table is (**channel_id**, **team_id**, **ts**).

## Relations

This table depends on [slack_conversations](slack_conversations).

The following tables depend on slack_conversation_histories:
  - [slack_conversation_replies](slack_conversation_replies)

## Columns

| Name          | Type          |
| ------------- | ------------- |
|_cq_id|`uuid`|
|_cq_parent_id|`uuid`|
|channel_id (PK)|`utf8`|
|team_id (PK)|`utf8`|
|ts (PK)|`utf8`|
|thread_ts|`utf8`|
|client_msg_id|`utf8`|
|type|`utf8`|
|channel|`utf8`|
|user|`utf8`|
|text|`utf8`|
|is_starred|`bool`|
|pinned_to|`list<item: utf8, nullable>`|
|attachments|`json`|
|edited|`json`|
|last_read|`utf8`|
|subscribed|`bool`|
|unread_count|`int64`|
|subtype|`utf8`|
|hidden|`bool`|
|deleted_ts|`utf8`|
|event_ts|`utf8`|
|bot_id|`utf8`|
|username|`utf8`|
|icons|`json`|
|bot_profile|`json`|
|inviter|`utf8`|
|topic|`utf8`|
|purpose|`utf8`|
|name|`utf8`|
|old_name|`utf8`|
|members|`list<item: utf8, nullable>`|
|reply_count|`int64`|
|reply_users|`list<item: utf8, nullable>`|
|parent_user_id|`utf8`|
|latest_reply|`utf8`|
|files|`json`|
|upload|`bool`|
|comment|`json`|
|item_type|`utf8`|
|reply_to|`int64`|
|team|`utf8`|
|reactions|`json`|
|response_type|`utf8`|
|replace_original|`bool`|
|delete_original|`bool`|
|metadata|`json`|
|permalink|`utf8`|