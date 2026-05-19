# Copilot Instructions

## Architecture

Hugo static site using the [LoveIt](https://github.com/dillonzq/LoveIt) theme (git submodule). Deployed to GitHub Pages via Actions on push to `main`. Custom domain: `philpalmieri.com`.

Content lives in Obsidian (`~/Documents/mind/Projects/Writing/`) and is copied here for publishing. Obsidian is the source of truth for all content.

### Content types

- **Posts** (`content/posts/`): Blog articles with front matter: title, slug, date, draft, description, tags, categories
- **Tools** (`content/tools/`): Tool/project pages linking to GitHub repos. Use archetype `archetypes/tools.md` which includes a `repo` front matter field and structured sections (What it does, Quick start)
- **About** (`content/about.md`): Static page

### Layout customizations

Custom layouts override the LoveIt theme:
- `layouts/tools/single.html` — full custom template for tool pages (mirrors post layout from theme)
- `layouts/partials/head/link.html` — adds custom CSS (`/css/custom.css`) and favicon links
- `layouts/robots.txt` — custom robots.txt template

## Local development

```bash
hugo server -D    # serves with drafts enabled at localhost:1313
hugo --minify     # production build to ./public
```

No test suite, linter, or build tooling beyond Hugo itself.

## Conventions

### Front matter

Posts use this pattern:
```yaml
title: "Human-readable Title"
slug: "url-friendly-slug"
date: 2026-05-14T08:30:00-04:00
draft: false
description: "SEO description"
tags: ["tag1", "tag2"]
categories: ["category"]
```

Tools add a `repo` field pointing to the GitHub repository URL.

### Security

- All GitHub Actions pinned to commit SHAs (no floating tags)
- `GITHUB_TOKEN` only (no PATs)
- Hugo `unsafe = true` in goldmark renderer (allows raw HTML in markdown content)

### Publishing workflow

1. Write/edit in Obsidian vault (`Projects/Writing/Blog/` for posts, `Projects/Writing/Tools/` for tools)
2. Copy content to this repo under `content/posts/` or `content/tools/`
3. Set `draft: false` and commit to `main`
4. GitHub Actions builds and deploys automatically
