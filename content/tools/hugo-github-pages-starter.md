---
title: "Hugo + GitHub Pages Starter"
slug: "hugo-github-pages-starter"
date: 2026-05-12T10:00:00-04:00
draft: false
repo: "https://github.com/philpalmieri/hugo-github-pages-starter"
tags: ["hugo", "github-pages", "github-actions", "blogging", "template"]
description: "A template repo for spinning up a Hugo blog on GitHub Pages with zero local tooling. Write markdown, push, it's live."
---

**GitHub Template:** [hugo-github-pages-starter](https://github.com/philpalmieri/hugo-github-pages-starter)

A minimal blog starter where the entire build happens in GitHub Actions. No local Hugo install, no Ruby, no Node. Write markdown, push to main, your site deploys in 30 seconds.

## What's in the box

- Hugo + LoveIt theme (pinned as git submodule)
- GitHub Actions workflow with SHA-pinned actions
- Minimal permissions, no PATs needed
- Post archetype with SEO fields (title, slug, date, tags, description)
- Custom domain + HTTPS instructions
- GoatCounter analytics support (optional)
- Page animations disabled, share buttons off, theme toggle hidden

## Quick start

```bash
# Use as template on GitHub, then clone your new repo
git clone --recurse-submodules https://github.com/YOUR_USERNAME/YOUR_REPO.git
```

Enable GitHub Pages (Settings > Pages > Source: "GitHub Actions"), push to main, done.

## Write a post

```markdown
---
title: "My Post"
slug: "my-post-url"
date: 2026-05-12T10:00:00-04:00
draft: false
tags: ["topic"]
description: "SEO description"
---

Your content here.
```

That's it. Push and it's live.
