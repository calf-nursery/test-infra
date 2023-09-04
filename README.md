# Prow

calf-nursery Prow dashboard: https://prow.calf-nursery.com

## Access Controls

- To merge, PRs must have `/approve` and `/lgtm`, which apply the `approved`
  and `lgtm` labels.
- The use of `/approve` and `/lgtm` is controlled by the `OWNERS` file in each
  repository where prow is running. See the [OWNERS spec](https://go.k8s.io/owners) for more details
  about how to manage access to all or part of a repo with this file.

See [Prow command help](https://prow.calf-nursery.com/command-help) for
more information about how to run each prow command.

## Prow commands

### External plugins

There are some plugins supported by prow and makes the life of the developer
easier in certain cases:

1. `cherry-pick` plugin can be used for cherrypicking PRs across branches by
   commenting:
   * **/cherry-pick branch-name** where `branch-name` is a branch, where the backport PR will be opened by the
     [kryton bot](https://github.com/apps/kryton-bot). Example:
      commenting **/cherry-pick release-0.1** on a PR targeting a *main* branch,
      a new cherry-pick PR will be opened against *release-0.1* branch of the same repo.
1. `needs-rebase` plugin manages the 'needs-rebase' label by removing it  from Pull Requests that are mergeable and adding it to those which are not.

### Built-in plugins

1. `override` plugin allows repo admins to force a github status context to pass by commenting: **/override job-name** on a PR. Example:
  commenting **/override test pull-rancher-turtles-build** on a PR
  will forcefully override the the given job and pass.
1. `retitle` allows users to re-title pull requests and issues where GitHub permissions don't allow them to by commenting: **/retitle new-PR-or-issue-title** on a PR/issue. Example:
  commenting **/retitle :book: Update README.md** on a PR
  will re-title pull request with new title provided.
1. `transfer-issue` plugin can be used for transferring issues across
   repositories in the same GitHub organization by commenting:
   * **/transfer-issue target-repo-name** on the issue.
     Example: commenting **/transfer-issue testapp** on an issue from *test-infra* repo should
      automagically transfer it to *testapp* repository.
