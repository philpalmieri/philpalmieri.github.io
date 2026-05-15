---
title: "How I Set Up This Blog Without Installing Anything Locally"
slug: "hugo-github-pages-no-local-install"
date: 2026-05-15
draft: false
tags: ["hugo", "github-pages", "github-actions", "blogging", "obsidian", "copilot"]
description: "A Hugo blog on GitHub Pages where I write in Obsidian, publish with Copilot, and never install a build tool locally."
---

I wanted a blog. I didn't want to manage one.

The requirements: write markdown in [Obsidian](https://obsidian.md/), tell my AI assistant to publish it, have it show up on my domain. No local [Hugo](https://gohugo.io/) install. No Ruby. No Node build step. No "oh wait, I'm on my other laptop and don't have the toolchain." Just markdown and a conversation.

## The workflow

1. Write in [Obsidian](https://obsidian.md/) (where I already live for notes, planning, everything)
2. Tell [Copilot CLI](https://github.com/features/copilot) to publish it
3. Copilot copies the markdown to the blog repo, sets up frontmatter, commits, pushes
4. [GitHub Actions](https://github.com/features/actions) builds the [Hugo](https://gohugo.io/) site and deploys to [Pages](https://pages.github.com/)

That's it. I never run Hugo. I never think about the build. I write, I say "publish," it's live in 30 seconds.

## The stack

- **[Hugo](https://gohugo.io/)** with the [LoveIt](https://github.com/dillonzq/LoveIt) theme
- **[GitHub Pages](https://pages.github.com/)** for hosting
- **[GitHub Actions](https://github.com/features/actions)** for the build (the only place Hugo runs)
- **[GoatCounter](https://www.goatcounter.com/)** for analytics (free, no cookies, no GDPR banners)
- Custom domain with HTTPS via GitHub's [Let's Encrypt](https://letsencrypt.org/) integration

Total cost: $0/month.

## Why no local build tools

I work from multiple machines. I didn't want "can I publish a blog post" to depend on whether I'd installed Hugo on that particular laptop. The entire build happens in Actions. If I can git push, I can publish.

This also means Copilot can do the publishing for me. It doesn't need Hugo installed either. It just needs to put the right markdown file in the right place and push.

## The Actions workflow

```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches: ["main"]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683
        with:
          submodules: recursive
          fetch-depth: 0

      - uses: peaceiris/actions-hugo@2752ce1d29631191ea3f27c23495fa06139a5b78
        with:
          hugo-version: "latest"
          extended: true

      - run: hugo --minify --baseURL "https://philpalmieri.com/"

      - uses: actions/upload-pages-artifact@56afc609e74202658d3ffba0e8f6dda462b719fa
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - uses: actions/deploy-pages@d6db90164ac5ed86f2b6aed7e0febac5b3c0c03e
```

Every action is pinned to a commit SHA (not a mutable tag). Minimal permissions. No PATs. The theme lives as a git submodule, also pinned to a specific commit.

## Why Obsidian as the writing layer

I already use [Obsidian](https://obsidian.md/) for everything: daily notes, 1:1 prep, project planning, technical breakdowns. Having blog drafts live in the same vault means I can link to research, pull from existing notes, and keep drafts alongside the thinking that led to them.

The blog repo doesn't know or care about Obsidian. It just receives markdown files with Hugo frontmatter. Obsidian is the authoring environment; the repo is the publishing target. Copilot is the bridge.

## What a "publish" looks like

When I'm done writing, I tell Copilot to publish. It:

- Copies the markdown from my Obsidian vault to the blog repo's `content/posts/` directory
- Converts any Obsidian-specific syntax (wikilinks, image embeds) to standard markdown
- Makes sure frontmatter is correct (title, slug, date, tags, description)
- Renames and copies any images to the static assets folder with SEO-friendly filenames
- Commits and pushes

One conversation, zero context switching. I stay in my writing environment the entire time.

## Custom domain setup

Standard GitHub Pages custom domain: four A records pointing to GitHub's IPs, a CNAME record for www, a `CNAME` file in the repo, and wait for the TLS cert to provision. Free HTTPS, automatic renewals.

## Analytics

[GoatCounter](https://www.goatcounter.com/). Free for personal use, privacy-respecting, gives me page views and referrers without tracking individuals. No cookie consent banner needed. LoveIt has native support, so it's one config line.

## Want to do the same thing?

I packaged this whole setup as a template repo: **[hugo-github-pages-starter](/tools/hugo-github-pages-starter/)**. Click "Use this template" on GitHub, enable Pages in your repo settings, push to main. You're live.
