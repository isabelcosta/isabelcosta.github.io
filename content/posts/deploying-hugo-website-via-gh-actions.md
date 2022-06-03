---
title: Deploy hugo website to GitHub Pages using GitHub Actions
date: '2022-06-03'
tags:
  - tech
  - open-source
---

The documentation on Hugo website is pretty good. But I did get confused with the branches that I had to enabled, so I will explain here how I got it to work for me.

Two things I had to get right were: GitHub Pages setup with deploy keys and the GitHub Actions setup.

## Setup the key SSH deploy key

To create the key for 
```bash
~/.ssh > ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f
~/.ssh > pbcopy < ~/.ssh/gh-pages 
~/.ssh > pbcopy < ~/.ssh/gh-pages.pub
```


## GitHub Actions `.workflows/gh-pages.yml` configuration

So by the end of many trials I got this to work:
```yml
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          deploy_token: ${{ secrets.ACTIONS_DEPLOY_KEY }}
          publish_dir: ./public
          publish_branch: gh-pages
```

For more details you can also check this documentation:
- https://gohugo.io/hosting-and-deployment/hosting-on-github/
- https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-create-ssh-deploy-key
