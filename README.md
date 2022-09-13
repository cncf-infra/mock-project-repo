# Prow Github Action test project repo

This repo has been created to **test and demo** the use of the prow-github-action, a custom github action that runs pga.

pga is under *active development as a proof of concept* [here](https://github.com/cncf-infra/prow-github-action/tree/27150) and is a go application that runs [Prow plugins](https://prow.k8s.io/plugins "links to Prow plugins catalog page") from [Github Actions](https://github.com/features/actions).

The intention is that you can *make use of Prow plugins* used on the Kubernetes project *without running your own Prow Instance*. 

Prow plugins are used for a variety of tasks that enhance and facility project workflow by interacting with Github to carry out tasks such as assigning reviewers to pull requests, managing OWNERS of code files and directories in a git repo in GITHUB and label management.

pga can be run from the following Custom Github Action
`docker://ghcr.io/cncf-infra/prow-github-action:latest`

You can see this in action on the [./github/workflow/comment.yaml](./github/workflow/comment.yaml)

```yaml
steps:
      - name: "Prow Github Actions for PR comment"
        env:
            NUMBER: ${{ github.event.issue.number }}
            REPO_OAUTH_TOKEN : ${{ secrets.GITHUB_TOKEN }}
            UNSPLASH_ACCESS_KEY : ${{ secrets.UNSPLASH_ACCESS_KEY }}
        uses: docker://ghcr.io/cncf-infra/prow-github-action:latest
```

## References

[Prow plugins](https://prow.k8s.io/plugins "links to Prow plugins catalog page")
[pga source code](https://github.com/cncf-infra/prow-github-action/tree/27150 "links to where pga is being developed") this is a fork of k8s.io/test-infra where Prow and other tools for the Kubernetes project are developed.
Creating [Custom Github Actions](https://docs.github.com/en/actions/creating-actions/about-custom-actions)
