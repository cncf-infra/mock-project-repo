# Prow Github Action test project repo

This repo has been created to **test and demo** the use of the prow-github-action, a custom github action that runs pga.

pga is under *active development as a proof of concept* [here](https://github.com/cncf-infra/prow-github-action/tree/27150) and is a go application that runs [Prow plugins](https://prow.k8s.io/plugins "links to Prow plugins catalog page") from [Github Actions](https://github.com/features/actions).

The intention is that you can *make use of Prow plugins* used on the Kubernetes project *without running your own Prow Instance*.

Prow plugins are used to assist in the review workflow by interacting with Github to carry out tasks such as assigning reviewers to pull requests, making use of [OWNERS files](https://www.kubernetes.dev/docs/guide/owners/) for git repos in Github and automatic label management on pull requests. These are just some examples of what Prow plugins can do if you want to use them.

pga  can be run from the following Custom Github Action
`docker://ghcr.io/cncf-infra/prow-github-action:latest`

You can see this working on the [./github/workflow/comment.yaml](./github/workflow/comment.yaml) Github Action


```yaml
steps:
      - name: "Prow Github Actions for PR comment"
        env:
            NUMBER: ${{ github.event.issue.number }}
            REPO_OAUTH_TOKEN : ${{ secrets.GITHUB_TOKEN }}
            UNSPLASH_ACCESS_KEY : ${{ secrets.UNSPLASH_ACCESS_KEY }}
        uses: docker://ghcr.io/cncf-infra/prow-github-action:latest
```

This then allows you to run the plugins that are present in the file https://github.com/cncf-infra/prow-github-action/blob/27150/prow/cmd/pga/kodata/plugins.yaml which is included in the ko built and published container, prow-github-action

## References

 - [Prow plugins](https://prow.k8s.io/plugins "links to Prow plugins catalog page")
 - [pga source code](https://github.com/cncf-infra/prow-github-action/tree/27150 "links to where pga is being developed") this is a fork of k8s.io/test-infra where Prow and other tools for the Kubernetes project are developed.
 - Creating [Custom Github Actions](https://docs.github.com/en/actions/creating-actions/about-custom-actions)
