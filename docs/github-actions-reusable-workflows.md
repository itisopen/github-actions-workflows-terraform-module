<!-- markdownlint-disable -->
## Workflows

| Name | Description |
|------|-------------|
| [Feature Branch (Pull Request) ChatOps for a Terraform Module](#feature-branch-pull-request-chatops-for-a-terraform-module) | ### Usage  |
| [Feature Branch (Pull Request) Workflow of a Terraform Module](#feature-branch-pull-request-workflow-of-a-terraform-module) | ### Usage  |
| [Release Branch Workflow of a Terraform Module](#release-branch-workflow-of-a-terraform-module) | ### Usage  |
| [Release Published Workflow of a Terraform Module](#release-published-workflow-of-a-terraform-module) | ### Usage  |
| [Scheduled Workflows of a Terraform Module](#scheduled-workflows-of-a-terraform-module) | ### Usage  |




## Feature Branch (Pull Request) ChatOps for a Terraform Module

### Usage 

In your repo create  __`.github/workflows/feature-branch-chatops.yml`__

```yaml
  name: feature-branch-chatops
  on:
    issue_comment:
      types: [created]
  
  permissions:
    pull-requests: write
    id-token: write
    contents: read
  
  jobs:
    terraform-module:
      uses: itisopen/github-actions-workflows-terraform-module/.github/workflows/feature-branch-chatops.yml@itisopen
      secrets:
        github_access_token: ${{ secrets.REPO_ACCESS_TOKEN }}
```



### Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| runs-on | Overrides job runs-on setting (json-encoded list) | string | ["ubuntu-latest"] | false |



### Secrets

| Name | Description | Required |
|------|-------------|----------|
| github\_access\_token | GitHub API token | true |






## Feature Branch (Pull Request) Workflow of a Terraform Module

### Usage 

In your repo create  __`.github/workflows/feature-branch.yml`__

```yaml
  name: feature-branch
  on:
    pull_request:
      branches: [ main ]
      types: [opened, synchronize, reopened, labeled, unlabeled]
  
  permissions:
    pull-requests: write
    id-token: write
    contents: read
  
  jobs:
    terraform-module:
      uses: itisopen/github-actions-workflows-terraform-module/.github/workflows/feature-branch.yml@itisopen
      secrets:
        github_access_token: ${{ secrets.REPO_ACCESS_TOKEN }}
```



### Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| runs-on | Overrides job runs-on setting (json-encoded list) | string | ["ubuntu-latest"] | false |



### Secrets

| Name | Description | Required |
|------|-------------|----------|
| REPO\_ACCESS\_TOKEN | GitHub API token | false |






## Release Branch Workflow of a Terraform Module

### Usage 

In your repo create  __`.github/workflows/release-branch.yml`__

```yaml
  name: release-branch
  on:
    push:
      branches:
        - main
        - release/**
  
  permissions:
    contents: write
    id-token: write
  
  jobs:
    terraform-module:
      uses: itisopen/github-actions-workflows-terraform-module/.github/workflows/release-branch.yml@itisopen
      secrets:
        github_access_token: ${{ secrets.REPO_ACCESS_TOKEN }}
```



### Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| runs-on | Overrides job runs-on setting (json-encoded list) | string | ["ubuntu-latest"] | false |



### Secrets

| Name | Description | Required |
|------|-------------|----------|
| REPO\_ACCESS\_TOKEN | GitHub API token | true |






## Release Published Workflow of a Terraform Module

### Usage 

In your repo create  __`.github/workflows/release.yml`__

```yaml
  name: release
  on:
    release:
      types:
        - published
  
  permissions:
    contents: write
    id-token: write
  
  jobs:
    terraform-module:
      uses: itisopen/github-actions-workflows-terraform-module/.github/workflows/release-published.yml@itisopen

```



### Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| runs-on | Overrides job runs-on setting (json-encoded list) | string | ["ubuntu-latest"] | false |








## Scheduled Workflows of a Terraform Module

### Usage 

In your repo create  __`.github/workflows/scheduled.yml`__

```yaml
  name: scheduled
  on:
    schedule:
      - cron: "0 3 * * *"

  permissions:
    pull-requests: write
    id-token: write
    contents: write
  
  jobs:
    scheduled:
      uses: itisopen/github-actions-workflows-terraform-module/.github/workflows/scheduled.yml@itisopen
      secrets:
        REPO_ACCESS_TOKEN: ${{ secrets.REPO_ACCESS_TOKEN }}
```



### Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| runs-on | Overrides job runs-on setting (json-encoded list) | string | ["ubuntu-latest"] | false |



### Secrets

| Name | Description | Required |
|------|-------------|----------|
| REPO\_ACCESS\_TOKEN | GitHub API token | true |





<!-- markdownlint-restore -->
