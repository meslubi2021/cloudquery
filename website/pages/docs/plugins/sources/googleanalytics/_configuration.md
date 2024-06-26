```yaml copy
kind: source
# Common source-plugin configuration
spec:
  name: googleanalytics
  path: cloudquery/googleanalytics
  registry: cloudquery
  version: "VERSION_SOURCE_GOOGLEANALYTICS"
  tables: ["*"]
  destinations: ["DESTINATION_NAME"]
  backend_options:
    table_name: "cq_state_googleanalytics"
    connection: "@@plugins.DESTINATION_NAME.connection"

  # Google Analytics specific configuration
  spec:
    property_id: "<YOUR_PROPERTY_ID_HERE>"
    oauth:
      access_token: "<YOUR_OAUTH_ACCESS_TOKEN>"
    reports:
    - name: example
      dimensions:
      - date
      - language
      - country
      - city
      - browser
      - operatingSystem
      - year
      - month
      - hour
      metrics:
      - name: totalUsers
      - name: new_users
        expression: newUsers
      - name: new_users2
        expression: "newUsers + totalUsers"
        invisible: true
      keep_empty_rows: true
```
