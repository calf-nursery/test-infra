# Prow

calf-nursey Prow dashboard: https://prow.calf-nursery.com

## Access Controls

- To merge, PRs must have `/approve` and `/lgtm`, which apply the `approved`
  and `lgtm` labels.
- The use of `/approve` and `/lgtm` is controlled by the `OWNERS` file in each
  repository prow is running. See the [OWNERS spec](https://go.k8s.io/owners) for more details
  about how to manage access to all or part of a repo with this file.

See the [Prow command help](https://prow.calf-nursery.com/command-help) for
more information about how to run each prow command.