## update-integration-environment
This repository is a GitHub workflow that is used to load services k8s definitions into the [integration-environment](https://github.com/get-fabric/integration-environment)

### Usage

To add a service to the integration environment folder add a file named `update-integration-environment.yaml` to your serivce github workflows:
```
name: update-integration-environment

on:
  push:
    paths:
      - 'deployment/**'
    branches: [main]

  workflow_dispatch:

jobs:
  update-integration-environment:
    uses: get-fabric/update-integration-environment/.github/workflows/update-integration-environment.yml@main
    with:
      service_name: ${{ github.event.repository.name }}
      namespace: YOUR_SERVICE_K8S_NAMESPACE
    secrets:
      git_token: ${{ secrets.ORG_GITHUB_ADMIN_TOKEN }}

```
Running this workflow will add `yaml` definition of your service into the [integration-environment](https://github.com/get-fabric/integration-environment/tree/main/deployments/fulfillment)
