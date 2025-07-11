# GFModules Trigger CI

- This pipeline is designed to trigger a TI (test integration) workflow for a GFModules project.
It will trigger the workflow and pass the necessary parameters.
- The pipeline is designed to be as generic as possible, so they can be easily reused in any project.
- This repository is a part of the generic GitHub Actions pipeline collection that can be used in any project.

## Usage

Here is a basic example of how you can integrate it in your project.

<details>
  <summary>Example workflow</summary>

This workflow is executed automatically on push to the main branch, except for dependabot merges.

```yml
name: GFModules Trigger CI

on:
  workflow_dispatch:
  pull_request:
  push:
    branches:
      - main

jobs:
  trigger-ci:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger CI
        uses: minvws/gfmodules-action-trigger-ci/.github/actions/gfmodules-trigger-ci@main
        with:
          orac_htpasswd: ${{secrets.ORAC_HTPASSWD}}
          endpoint_url: ${{URL}}
```

</details>

### Configuration

The action has inputs. The inputs are:

- orac_htpasswd: The HTPassword for the ORAC endpoint. This is a secret and should be stored in the repository secrets. It should be in the format of `user:pass`.
- endpoint_url: The URL of the ORAC endpoint. This is a required input and should be provided as a string.

### Update the bundle

When making changes in the src/index.js, make sure you generate the bundle by running `npm run bundle`

## Contributing

If you want to contribute a new pipeline, please check the reusable workflow guidelines in the
[GitHub documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows#creating-a-reusable-workflow).
