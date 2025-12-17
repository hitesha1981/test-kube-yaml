# test-kube-yaml
# Author: Hitesh Agrawal
```
To test whether the deployment files are proper yaml and will deploy properly on kubernetes via github actions.
Catch any errors in your yaml before they hit your kubernetes cluster.
Please check .github/workflows/ci.yaml in this repo.
If you want to have same checks for your repo, add below to your github actions as .github/workflows/kubechecks.yaml
Update the kube version below to your kubernetes cluster version
```
```bash
---
name: Test yamllint and kubeconform
on:
  push:
    branches:
      - main
    paths:
      - '**.yaml'
      - '**.yml'
  pull_request:
    paths:
      - '**.yaml'
      - '**.yml'
  workflow_dispatch: # Allows manual triggering

jobs:
  lint-and-validate:
    # Points to central ci-template repo
    uses: hitesha1981/ci-templates/.github/workflows/kubeconform.yaml@main
    with:
      kube_version: "1.31.0"
      strict: true
```
