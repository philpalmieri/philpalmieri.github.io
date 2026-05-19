---
title: "Engineering Manager Skills"
slug: "engineering-manager-skills"
date: 2026-05-19T12:30:00-04:00
draft: false
repo: "https://github.com/philpalmieri/engineering-manager-skills"
tags: ["copilot", "AI", "engineering-management", "obsidian", "github", "skills", "productivity"]
description: "A collection of 28 reusable Copilot CLI skills that turn your terminal into a chief of staff. 1:1 prep, team metrics, sprint tracking, weekly snippets, and more."
---

**GitHub Repo:** [engineering-manager-skills](https://github.com/philpalmieri/engineering-manager-skills)

A collection of 28 reusable [Copilot CLI skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) for engineering managers who use Obsidian as their PKM and GitHub for team management. Talk to Copilot like you'd talk to a chief of staff.

## What it does

You type things like:

```
> prep my day
> prep 1:1 with Sam
> write my weekly snippet
> how's the team doing?
> review network for last month
> generate review cards for Q3
```

Behind each prompt is a skill that knows where to look, what to fetch, and how to format the output. Skills pull from GitHub (PRs, reviews, issues, sprints), your Obsidian vault (daily notes, people files, open tasks), and a local `team.json` config.

No new apps. No dashboards. No manual data entry. Just conversation.

## What's included

28 skills across 6 categories:

- **Obsidian** — task rollover, daily note management, vault operations
- **GitHub** — team activity sync, PR enrichment, sprint tracking, epic management
- **Management** — 1:1 prep (direct reports + peers), weekly snippets, interview prep, project status
- **Technical** — product briefs, codebase deep dives, initiative breakdowns
- **Metrics** — review network analysis, contribution velocity, 9-box grids, team health dashboards
- **Orchestration** — end-to-end workflows that chain skills together (like `prep-my-day`)

## Quick start

```bash
# Ask Copilot directly
> install skills from philpalmieri/engineering-manager-skills

# Or clone and symlink
gh repo clone philpalmieri/engineering-manager-skills ~/Dev/engineering-manager-skills

for skill in ~/Dev/engineering-manager-skills/skills/*/*; do
  ln -sf "$skill" ~/.copilot/skills/$(basename "$skill")
done
```

Then configure your team:

```
> setup my team config
> sync my team data
> prep my day
```

## How it's built

Skills are layered and composable. Data flows from `gh` CLI through fetch/enrich skills into local JSON, then metrics and management skills consume that data to produce reports, prep docs, and vault updates. All org-specific config lives in a single `team.json` file (gitignored), so the skills themselves contain zero personal data and are safe to share.

## Prerequisites

- [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)
- [GitHub CLI (`gh`)](https://cli.github.com/) authenticated with org access
- An Obsidian vault with daily notes and people files
