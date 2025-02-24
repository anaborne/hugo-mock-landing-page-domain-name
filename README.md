# hugo-mock-landing-page
- a landing page for a food inventory tracking application concept 'Freshli'
using Hugo and a bootstrap theme

# GitHub Actions Workflow

This repository uses a GitHub Actions workflow to automatically build and deploy a Hugo website to GitHub Pages.

## Workflow Overview

The workflow, named "🏗️ Build and Deploy GitHub Pages," triggers automatically whenever code is pushed to the `main` branch. It handles the complete build and deployment process in a single job.

```yaml
name: 🏗️ Build and Deploy GitHub Pages
on:
  push:
    branches:
      - main # Set a branch to deploy
```

## Build Process

The workflow:

1. Checks out the repository code including all submodules (needed for Hugo themes)
2. Sets up Hugo version 0.144.1 (extended version)
3. Builds the static website with draft content included and file minification
4. Deploys the built site to the `gh-pages` branch

## Key Commands

The Hugo build command used:
```yaml
run: hugo -D --gc --minify
```
- `-D`: includes draft content
- `--gc`: runs garbage collection
- `--minify`: minimizes the output files

## Deployment Configuration

The workflow publishes to GitHub Pages with these settings:
```yaml
uses: peaceiris/actions-gh-pages@v3.9.3
with:
  github_token: ${{ secrets.GITHUB_TOKEN }}
  publish_branch: gh-pages
  user_name: "github-actions[bot]"
  user_email: "github-actions[bot]@users.noreply.github.com"
```

For custom domains, uncomment the `cname` parameter in the workflow file.
