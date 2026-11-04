# Patchnotes

A single-page dashboard for meaningful AI coding-tool updates. It is dependency-free and runs as a static site.

## Features

- Curated highlights with short editorial context and links to first-party sources.
- Search, category and date filters, plus per-tool filtering.
- Followed tools saved in the current browser with `localStorage`.
- Public release notes from the GitHub releases for Claude Code, Codex, Cline, and Gemini CLI.
- Preview releases labeled separately; unreviewed release notes appear in **All updates**, not the curated highlights.
- Release API responses cached in the browser for six hours. If a feed is unavailable, the dashboard uses that feed's cached releases when available.

## Run locally

From the repository root:

```powershell
python -m http.server 4173 --bind 127.0.0.1
```

Open <http://127.0.0.1:4173>. No build step, dependencies, API keys, or paid services are required.

## Data sources and limitations

Live release feeds use GitHub's unauthenticated public API:

- [Claude Code releases](https://github.com/anthropics/claude-code/releases)
- [OpenAI Codex releases](https://github.com/openai/codex/releases)
- [Cline releases](https://github.com/cline/cline/releases)
- [Gemini CLI releases](https://github.com/google-gemini/gemini-cli/releases)

Curated highlights are maintained in `index.html` from the official [Cursor changelog](https://cursor.com/changelog), [VS Code updates](https://code.visualstudio.com/updates), and [Devin Desktop changelog](https://docs.devin.ai/desktop/changelog). Those pages do not currently use the same release API integration. Cursor's changelog does not consistently show an item-level date, so those entries are marked **Date not listed** and won't match date-range filters.

GitHub API limits apply per visitor IP. The dashboard caches successful feed responses in each browser for six hours; manual refresh bypasses that cache and can make additional requests. Live feeds are best-effort, not a completeness guarantee. Check each linked publisher source for current availability and details.

## Free static hosting

`.github/workflows/pages.yml` publishes this static site to GitHub Pages whenever `feature-development` is pushed. GitHub Pages can host public repositories on its free plan. To publish, push this branch to a GitHub repository, enable **Settings → Pages → Build and deployment → GitHub Actions**, and allow the workflow to run. The current local repository has no GitHub remote; publishing requires an authenticated GitHub account and a public repository, which makes the source code public.

## Delivery record

See [COMPLETION.md](./COMPLETION.md) for the time spent and completed work.
