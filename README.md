# Publish to Cloudflare Pages via POST

Deploy your Cloudflare site using your deploy hook (and a secret curl POST request)

## Usage

1. Create a new Cloudflare Pages site
2. Create a new secret in your repository called `DEPLOY_HOOK_URL` with the value of your deploy hook URL
3. Optionally, set the shell to be used by the action (default: `bash`) by using the `shell` input parameter
4. Finally, add the following to your workflow:

```yaml
name: Deploy to Cloudflare Pages

on:
  push:
    branches:
      - [INSERT BRANCH NAME HERE] # This will trigger the workflow only when you push to this branch
    workflow_dispatch: # This allows you to manually trigger the workflow from the Actions tab

env:
  shell: bash # Optional, defaults to bash

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: TheModdersDen/cloudflare-pages-deploy-action@v1
        with:
          DEPLOY_HOOK_URL: ${{ secrets.DEPLOY_HOOK_URL }}
```
