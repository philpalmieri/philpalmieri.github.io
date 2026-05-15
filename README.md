# philpalmieri.github.io

Personal blog, built with Hugo + [LoveIt](https://github.com/dillonzq/LoveIt) theme, deployed via GitHub Pages.

## How it works

- Write markdown in Obsidian (`Writing/Published/`)
- Push to this repo (manually or via Copilot "publish my writing" skill)
- GH Actions builds with Hugo and deploys to GitHub Pages
- Custom domain: `philpalmieri.com`

## Security

- All GH Actions pinned to commit SHAs (no tag references)
- No third-party actions with write access
- `GITHUB_TOKEN` only (no PATs)
- Hugo runs with `unsafe = false` (no raw HTML injection in markdown)
- `.nojekyll` disables Jekyll processing

## Local preview (optional)

```bash
brew install hugo
hugo server -D
```

Not required for publishing; all builds happen in Actions.
