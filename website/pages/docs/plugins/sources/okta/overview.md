---
name: Okta
stage: GA
title: Okta Source Plugin
description: CloudQuery Okta source plugin documentation
---
# Okta Source Plugin

:badge

The CloudQuery Okta plugin extracts data from your Okta domain and loads it into any supported CloudQuery destination (e.g. PostgreSQL, BigQuery, Snowflake, and [more](/docs/plugins/destinations/overview)).

## Authentication

:authentication

## Configuration

The following example sets up the Okta plugin, and connects it to a postgresql destination:

:configuration

:::callout{type="info"}
Make sure you use [environment variable expansion](/docs/advanced-topics/environment-variable-substitution) in production instead of committing the credentials to the configuration file directly.
:::

- `domain` (`string`, required)

  Specify the Okta domain you are fetching from.
  [Visit this link](https://developer.okta.com/docs/guides/find-your-domain/findorg/) to find your Okta domain.

- `token` (`string`, optional)

  Token for Okta API access.
  You can set this with an `OKTA_API_TOKEN` environment variable.
  :::callout{type="warning"}
  Using `OKTA_API_TOKEN` environment variable will be deprecated in the future versions.
  You can use [environment variable expansion](/docs/advanced-topics/environment-variable-substitution) and `"${OKTA_API_TOKEN}"` value in the configuration instead.
  :::

- `debug` (`bool`, optional. Default: `false`)

  Enables debug logs within the Okta SDK.
  :::callout{type="warning"}
  This feature will result in sensitive information being logged!
  :::

- `concurrency` (`integer`, optional. default: `10000`)

  Number of concurrent requests to be made to Okta API.

- `rate_limit` ([Rate limit](#rate-limit-spec) spec, optional. Default: see [rate limit](#rate-limit-spec) spec defaults)

  Rate limit configuration.

### Rate limit spec

- `max_backoff` (`duration`, optional. Default: `5s`)

  Max backoff interval to be used.
  If the value specified is less than the default one, the default one is used.

- `max_retries` (`int32`, optional. Default: `3`)

  Max retries to be performed.
  If the value specified is less than the default one, the default one is used.

## Example Queries

### List all users in Okta

```sql copy
select 
  id,
  profile->>'firstName' as first_name,
  profile->>'lastName' as last_name,
  profile->>'email' as email,
  status
from okta_users;
```

### List all active users

```sql copy
select
  id,
  profile->>'firstName' as first_name,
  profile->>'lastName' as last_name,
  profile->>'email' as email,
  status from okta_users
where
  status = 'ACTIVE';
```

### List active Okta applications

```sql copy
select
  id,
  name
from
  okta_applications
where status = 'ACTIVE';
```

### List active Okta applications, ordered by number of users

```sql copy
select 
  a.id,
  a.name,
  a.status,
  count(u) 
from okta_applications a 
  left join okta_application_users u 
    on u.app_id = a.id 
group by a.id, a.name
order by count desc;
```
