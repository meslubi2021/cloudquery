```yaml copy
kind: source
# Common source-plugin configuration
spec:
  name: typeform
  registry: docker
  path: ghcr.io/cloudquery/cq-source-typeform:VERSION_SOURCE_TYPEFORM
  tables: ["typeform_forms"]
  destinations: ["DESTINATION_NAME"]
  # Typeform-specific configuration
  spec:
    access_token: "<YOUR_SECRET_ACCESS_TOKEN_HERE>"
    base_url: "https://api.typeform.com" # use https://api.eu.typeform.com for EU accounts
    # Optional configuration
    # concurrency: 100
    # queue_size: 10000
```

:::callout{type="info"}
The Typeform plugin is distributed as a Docker image. This requires a Docker runtime to be installed on the same machine as the CloudQuery CLI, and a CLI version that supports the `docker` registry type (`v3.12.0` and higher).
:::