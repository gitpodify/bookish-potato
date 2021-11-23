# This repository exists so people can test their contributions to <https://gitlab.com/gitpodify/gitpodified-workspace-images> and <https://github.com/gitpod-io/workspace-images> easily.

First, fork this repository using these links to get started, depending on which Git host are you currently using right now:

* [GitHub](https://github.com/gitpodify/bookish-potato/fork)
* [GitLab SaaS](https://gitlab.com/gitpodify/bookish-potato/fork)

## How this works? - Gitpodified Workspace Images

1. Right after creating an merge request or pushing coommits to your fork's source branch, copy the following command to trigger an build. If the build doesn't shows up after 10-20 minutes, check <https://recaptime-workspace-images-artifacts-hook.builtwithdark.com/gitlab/pipelines> and drill down the pipeline ID our bots provided if things start to break. (Please do noit spam the command below to avoid rate-limiting chaos.)

```
@RecapTimeBot rebuild image
```

2. Change line 3 of your `.gitpod.yml`, replacing `id` with the merge request ID (e.g. `1234` if your merge request ID is `1234`).

```yml
image: quay.io/recaptime-dev/gitpod-workspace-images-artifacts:gl-gitpodify-gitpod-workspace-images-mr-1234
```

3. Commit to an seperate branch, usually in form of `gitpodify/test-pr-<id>` and open that branch in Gitpod.

4. If everything is fine, wait for the maintainer's approval. Otherwise, nuke that workspace, fix it and repeat.

## How this works? - Official Gitpod Workspace Images / Contributing to Upstream

1. After submitting your pull request, tag an maintainer, usually an Gitpod team member, to manually trigger CI builds on Circle CI.

2. Change line 3 of your `.gitpod.yml`, replacing `quay.io/recaptime-dev/gitpod-workspace-images-artifacts:gl-gitpodify-gitpod-workspace-images-mr-id` with the following format where `123` is your pull request ID.

```yml
image: gitpod/workspace-full:branch-pr-123
```

3. Commit to an seperate branch, usually in form of `gitpod-io/test-pr-<id>` and open that branch in Gitpod.

4. If everything is fine, wait for the maintainer's approval. Otherwise, nuke that workspace, fix it and repeat. Remember to annoy them again after you push changes/fixes.