---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "grafana_team_external_group Resource - terraform-provider-grafana"
subcategory: "Grafana Enterprise"
description: |-
  Use the team_sync attribute of the grafana_team resource instead.
---

# grafana_team_external_group (Resource)

Use the `team_sync` attribute of the `grafana_team` resource instead.

## Example Usage

```terraform
resource "grafana_team_external_group" "test-team-group" {
  team_id = 1
  groups = [
    "test-group-1",
    "test-group-2"
  ]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `groups` (Set of String) The team external groups list
- `team_id` (String) The Team ID

### Read-Only

- `id` (String) The ID of this resource.

## Import

Import is supported using the following syntax:

```shell
terraform import grafana_team_external_group.main {{team_id}}
```
