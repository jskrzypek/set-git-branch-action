# Set Git Branch

This is a dead-simple composite action that uses the github context to provide
an environment variable (`$GIT_BRANCH`) and an output (`branch-name`) with the
branch name that workflow creators are most likely to care about.

## Pull Request Events

For Pull Request events (`pull_request` & `pull_request_target`) the `github`
context provides the `github.head_ref` context variable that contains the name
of the source branch for the PR.

## Other `branch`-type Events

For other events triggered by branches, the [`github`
context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context)
provides the `github.ref_name` variable with the name of the branch or tag that
triggered the event, and this is what is used to set the env var & output

## Tag Events

Whenever `github.ref_type` is set to `tag`, the current event was triggered by a
tag, and the `github` context does not provide any branch-relevant information,
so this action provides an empty output and environment variable.
