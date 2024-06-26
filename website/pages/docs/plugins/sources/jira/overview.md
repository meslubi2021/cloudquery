---
name: Jira
stage: Preview (Open Core)
title: Jira Source Plugin
description: CloudQuery Jira source plugin documentation
---
# Jira Source Plugin

:badge

:badge{text="Open Core"}

This is an open-core plugin with set of free tables available and full version that you can buy [here](/integrations/jira).

The CloudQuery Jira plugin extracts Jira information and loads it into any supported CloudQuery destination (e.g. PostgreSQL, BigQuery, Snowflake, and [more](/docs/plugins/destinations/overview)). It is based on the [Jira API](https://developer.atlassian.com/cloud/jira/platform/rest/v3/) and the [`github.com/andygrunwald/go-jira`](https://github.com/andygrunwald/go-jira) library.

## Authentication

:authentication

## Configuration

The following example sets up the Jira plugin, and connects it to a postgresql destination:

:configuration

### Jira Spec

This is the specs that can be used by the Jira source Plugin.

- `base_url` (`string`, required.)

  Your Jira base URL. For hosted versions URI is `https://your_account_name.atlassian.net/`

- `username` (`string`, required.)

  The username to authenticate with.

- `token` (`string`, required.)

  Personal access to authenticate with (recommendation: Use environment variable instead of hardcoded the token in the config).
