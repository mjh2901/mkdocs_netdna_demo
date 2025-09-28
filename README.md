mkdocs_netdna_demo
===================

This repository contains documentation for the mkdocs_netdna_demo site and is configured to publish to GitHub Pages using GitHub Actions.

Setup (local)
---------------

1. Initialize git and create your first commit (this will create the repository locally):

```bash
git init
git add .
git commit -m "Initial commit: MkDocs site and CI workflow"
```

2. Create the remote repository on GitHub (you must have the GitHub CLI `gh` installed and authenticated, or create the repo on the website). Using `gh`:

```bash
gh repo create mjh2901/mkdocs_netdna_demo --public --source=. --remote=origin --push
```

If you don't have `gh`, create the repo on github.com under `mjh2901` and add the remote manually:

```bash
git remote add origin git@github.com:mjh2901/mkdocs_netdna_demo.git
git branch -M main
git push -u origin main
```

3. After pushing, GitHub Actions will run the workflow and deploy the built site to GitHub Pages (the action uses `peaceiris/actions-gh-pages`). The site will be published from the `gh-pages` branch by the action.

Local preview
--------------

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install mkdocs mkdocs-material pymdown-extensions
mkdocs serve
```

Notes
-----
- The Docker Compose file mounts the repository into the `mkdocs` container at `/docs`, which is convenient for containerized previews.
- This repo assumes `main` as the default branch. The workflow triggers on pushes to `main` or `master`.
