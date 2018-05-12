# terraform-provider-circleci

[![Join the chat at https://gitter.im/thiagoalessio/terraform-provider-circleci](https://badges.gitter.im/thiagoalessio/terraform-provider-circleci.svg)](https://gitter.im/thiagoalessio/terraform-provider-circleci?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[Terraform][] provider for [CircleCI][].

[![Codacy][codacy_badge]][codacy]
[![Code Coverage][coverage_badge]][codacy]

## Provider

The CircleCI provider is used to interact with CircleCI resources.

The provider allows you to manage your CircleCI projects and their environment
variables easily. It needs to be configured with the proper credentials before
it can be used.

#### Example Usage

```hcl
provider "circleci" {
  token        = "${var.circleci_token}"
  organization = "${var.circleci_organization}"
}
```

#### Argument Reference

The following arguments are supported in the `provider` block:

* `token` - (Optional) This is the CircleCI API token. It must be provided,
  but it can also be sourced from the `CIRCLECI_TOKEN` environment variable.

* `organization` - (Optional) This is the organization/account to be managed.
  It must be provided, but it can also be sourced from the `CIRCLECI_ORGANIZATION`
  environment variable.

---

## Data Sources

@TODO

---

## Resources

### circleci_project

Provides a CircleCI project resource.

This resource allows you to start/stop building projects from your organization.
When applied, a project is enabled. When destroyed, that project will be disabled.

#### Example Usage

```hcl
resource "circleci_project" "myproj" {
  name = "myproj"

  env_vars {
    SOME_TOKEN = "a1b2c3d4e5f6g7h8i9j0"
  }
}
```

#### Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the project/repository.

* `env_vars` - (Optional) A mapping of environment variables to assign to the
  resource.

#### Import

CircleCI projects can be imported using the name, e.g.

```shell
$ terraform import circleci_project.myproj myproj
```

## License

terraform-provider-circleci is released under the [Mozilla Public License 2.0][].


<h2></h2><p align="center"><sub>Made with <sub><a href="#"><img src="https://thiagoalessio.ams3.digitaloceanspaces.com/heart.svg" alt="love" width="14px"/></a></sub> in Berlin</sub></p>

[Terraform]: https://www.terraform.io
[CircleCI]: https://circleci.com
[codacy_badge]: https://api.codacy.com/project/badge/Grade/f6d223a6d8ad4ea6b0a65d5c5235f5fc
[codacy]: https://www.codacy.com/app/thiagoalessio/terraform-provider-circleci
[coverage_badge]: https://api.codacy.com/project/badge/Coverage/f6d223a6d8ad4ea6b0a65d5c5235f5fc
[Mozilla Public License 2.0]: https://github.com/thiagoalessio/terraform-provider-circleci/blob/master/LICENSE
