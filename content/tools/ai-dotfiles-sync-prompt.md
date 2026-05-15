---
title: "AI Dotfiles Sync Prompt"
slug: "ai-dotfiles-sync-prompt"
date: 2026-05-08T09:00:00-04:00
draft: false
tags: ["dotfiles", "AI", "copilot", "chezmoi", "devx", "terminal"]
description: "A single prompt you paste into any AI CLI tool to backup and sync all your AI tool configs, shell settings, and dotfiles with chezmoi."
---

**Gist:** [dotfiles-setup-prompt](https://gist.github.com/philpalmieri/c9d7f2c4badcc4a6931902b7f5f32670)

A single prompt you paste into any AI assistant with terminal access ([GitHub Copilot CLI](https://github.com/features/copilot), [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Cursor](https://cursor.sh/)) and it will discover, backup, and sync your entire dev environment using [chezmoi](https://www.chezmoi.io/).

## What it does

- Discovers AI tool configs (Copilot CLI, Claude Code, Cursor, custom instructions, memory files)
- Finds shell configs, git settings, editor preferences
- Sets up chezmoi to manage everything in a single git repo
- Handles templates for machine-specific differences
- Works on macOS and Linux

## How to use it

1. Copy the prompt from the gist
2. Paste it into your AI CLI tool of choice
3. Let it scan your system and set up chezmoi
4. Push to a private GitHub repo for cross-machine sync

## Related

- [Blog post: Your AI Tools Have Dotfiles Too](/posts/your-ai-tools-have-dotfiles-too/)
