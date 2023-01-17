---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "grafana_data_source Data Source - terraform-provider-grafana"
subcategory: "Grafana OSS"
description: |-
  Get details about a Grafana Datasource querying by either name, uid or ID
---

# grafana_data_source (Data Source)

Get details about a Grafana Datasource querying by either name, uid or ID

## Example Usage

```terraform
resource "grafana_data_source" "prometheus" {
  type                = "prometheus"
  name                = "prometheus-ds-test"
  uid                 = "prometheus-ds-test-uid"
  url                 = "https://my-instance.com"
  basic_auth_enabled  = true
  basic_auth_username = "username"

  json_data_encoded = jsonencode({
    httpMethod        = "POST"
    prometheusType    = "Mimir"
    prometheusVersion = "2.4.0"
  })

  secure_json_data_encoded = jsonencode({
    basicAuthPassword = "password"
  })
}

data "grafana_data_source" "from_name" {
  name = grafana_data_source.prometheus.name
}

data "grafana_data_source" "from_id" {
  id = grafana_data_source.prometheus.id
}

data "grafana_data_source" "from_uid" {
  uid = grafana_data_source.prometheus.uid
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `name` (String)
- `uid` (String)

### Read-Only

- `access_mode` (String) The method by which Grafana will access the data source: `proxy` or `direct`.
- `basic_auth_enabled` (Boolean) Whether to enable basic auth for the data source.
- `basic_auth_username` (String) Basic auth username.
- `database_name` (String) (Required by some data source types) The name of the database to use on the selected data source server.
- `id` (String) The ID of this resource.
- `is_default` (Boolean) Whether to set the data source as default. This should only be `true` to a single data source.
- `json_data_encoded` (String) Serialized JSON string containing the json data. This attribute can be used to pass configuration options to the data source. To figure out what options a datasource has available, see its docs or inspect the network data when saving it from the Grafana UI. Note that keys in this map are usually camelCased.
- `type` (String) The data source type. Must be one of the supported data source keywords.
- `url` (String) The URL for the data source. The type of URL required varies depending on the chosen data source type.
- `username` (String) (Required by some data source types) The username to use to authenticate to the data source.

