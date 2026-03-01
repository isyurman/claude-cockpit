# Changelog

All notable changes to Claude Cockpit will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

### Added

- **Cost breakdown formula** — Click any session's cost to see tokens × rate = cost for each token type (input, output, cache write, cache read), with multi-model detection
- **Per-model cost chart** — Metrics dashboard shows cost by model with Anthropic's official rates inline and a verifiable total sum
- **Session ID search** — Search by session UUID prefix (3+ chars, with or without dashes) — ID matches rank above fuzzy results
- **Complete model coverage** — Added pricing for Opus 4.1, Sonnet 4, Sonnet 3.7, Haiku 3, and Opus 3

### Fixed

- **Opus fallback pricing** — Unknown opus models now default to $15/MTok tier (not $5) — prevents 3× undercounting for Opus 4.0/4.1 sessions
- **Multi-model session cost** — `totalCost` now sums per-API-call costs instead of recalculating from first model seen, fixing incorrect totals for sessions that switch models

## [0.1.0] - 2026-03-01

### Added

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
- **Session Comparison** — Compare two sessions side-by-side across 13 metrics
- **Virtual Scrolling** — Smooth performance with hundreds of sessions
- **Smart Indexing** — Automatic discovery and incremental re-indexing of JSONL session files
