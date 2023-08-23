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

## Prow commands

There are some plugins supported by prow and makes the life of the developer
easier in certain cases:

1. `cherry-pick` plugin can be used for cherrypicking PRs across branches by
   commenting:
   * **/cherry-pick branch-name** where `branch-name` is a branch, where the backport PR will be opened by the
     [kryton bot](https://github.com/apps/kryton-bot). Example:
      commenting **/cherry-pick release-0.1** on a PR targeting a *main* branch,
      a new cherry-pick PR will be opened against *release-0.1* branch of the same repo.
1. `transfer-issue` plugin can be used for transferring issues across
   repositories in the same GitHub organization by commenting:
   * **/transfer-issue target-repo-name** on the issue.
     Example: commenting **/transfer-issue testapp** on an issue from *calf-test-infra* should
      automagically transfer it *testapp* repository.