# GFModules Trigger CI GitHub Action

This repository provides a reusable GitHub Action for triggering a TI (test integration) workflow for a GFModules project. It will trigger the workflow and pass the necessary parameters.

## Usage

To use the action, add it to a workflow in your repository:

Here is a basic example of how you can integrate it in your project.

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
        uses: minvws/gfmodules-action-trigger-ci@v1
        with:
          orac_htpasswd: ${{ secrets.ORAC_HTPASSWD }}
          endpoint_url: <url>
```

Replace `<url>` with the URL of the ORAC endpoint.

In this basic example, the workflow is executed automatically on push to the `main` branch and on any pull request. And thanks to the `workflow_dispatch` trigger it can also be executed manually from the repository's Actions tab.

### Configuration

The action has the following inputs:

- `orac_htpasswd` (**required**): The HTPassword for the ORAC endpoint, formatted as `"user:pass"`. This should be stored in the repository secrets.
- `endpoint_url` (**required**): The URL of the ORAC endpoint.

### Update the bundle

When making changes in the src/index.js, make sure you generate the bundle by running `npm run bundle`

## Contributing

If you want to contribute a new pipeline, please check the reusable workflow guidelines in the
[GitHub documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows#creating-a-reusable-workflow).

## License

This repository is released under the EUPL 1.2 license. See [LICENSE](./LICENSE) for details.
