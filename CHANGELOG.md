# Changelog

All notable changes to Claude Cockpit will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

## [0.2.4] - 2026-03-01

### Improved

- **2x Retina screenshots** — All marketing screenshots recaptured at 2x DPI for crisp display on HiDPI screens
- **Automated screenshot pipeline** — Playwright-based capture script for reproducible marketing assets
- **Deploy scripts** — One-command release workflow for packaging and deploying to both repos

## [0.2.3] - 2026-03-01

### Added

- **Cost breakdown formula** — Click any session's cost to see tokens × rate = cost for each token type (input, output, cache write, cache read), with multi-model detection
- **Per-model cost chart** — Metrics dashboard shows cost by model with Anthropic's official rates inline and a verifiable total sum
- **Session ID search** — Search by session UUID prefix (3+ chars, with or without dashes) — ID matches rank above fuzzy results
- **Tag autocomplete** — Combobox dropdown suggests existing tags when adding tags to sessions
- **Unified date filters** — Consistent date chip selector (Today, 7d, 30d, 90d, Range, All) across Sessions, Metrics, and Timeline tabs

### Fixed

- **Opus fallback pricing** — Unknown opus models now default to $15/MTok tier (not $5), preventing undercounting for Opus 4.0/4.1 sessions
- **Multi-model session cost** — Total cost now sums per-API-call costs correctly for sessions that switch models mid-conversation
- **Complete model coverage** — Added pricing for Opus 4.1, Sonnet 4, Sonnet 3.7, Haiku 3, and Opus 3

## [0.1.0] - 2026-03-01

Initial release.

- **Session Dashboard** — Browse all Claude Code sessions with search, filters, and sorting
- **Full-text search** — Multi-word fuzzy search across session names, summaries, tools, files, and tags
- **Pin & Tag** — Pin important sessions, add custom tags for quick retrieval
- **Session Notes** — Add notes to any session for future reference
- **Quick Resume** — Resume sessions in VS Code terminal, iTerm2, Terminal.app, Alacritty, WezTerm, or Warp
- **Auto-approve mode** — Resume with `-y` flag for unattended execution
- **Session Preview** — Full detail view with cost breakdown, sampled messages, and notes
- **Prompt Library** — Save, edit, and reuse prompt templates with categories and use tracking
- **Usage Metrics** — Track sessions, messages, tokens, and costs by model and project
- **Timeline View** — Visualize session activity over time, color-coded by project
- **Cross-Device Sync** — Pins, tags, notes, and prompts sync across devices via VS Code Settings Sync
- **Keyboard Shortcuts** — Navigate with arrow keys, `r` to resume, `p` to pin, `Ctrl+K` to search
- **Export/Import** — Back up all user data to JSON and restore on any machine
