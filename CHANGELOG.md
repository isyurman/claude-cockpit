# Changelog

All notable changes to Claude Cockpit will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

## [0.4.2] - 2026-03-02

### Fixed

- **Critical: infinite re-indexing loop** — Sessions without `cwd` were re-parsed every indexing cycle (~60 files every 2-5 seconds), causing memory to grow to 8GB+. Removed `hasMissingCwd` check from re-index conditions
- **Concurrent indexing races** — Added lock to prevent overlapping `indexAll()` runs when watcher fires during an active index

## [0.4.1] - 2026-03-02

### Fixed

- **Pinned filter behavior** — Toggling Pinned pill OFF now hides pinned sessions from the list. Previously pinned sessions always appeared regardless of filters
- **Memory: streaming indexer** — `parseSessionMeta` now streams JSONL files line-by-line instead of loading entire files into memory (fixes rising memory on large session files)
- **Memory: watcher debounce** — File watcher debounces at 2 seconds to prevent rapid re-indexing during active Claude sessions
- **Memory: status bar** — Status bar uses `count()` + targeted cost query instead of loading all session objects

## [0.4.0] - 2026-03-02

### Added

- **Logging infrastructure** — OutputChannel logger ("Claude Cockpit") with timestamped info/warn/error. Logs activation, indexing stats, preview parsing, and insight generation

### Fixed

- **Preview scroll** — Entire preview body (actions, tags, cost breakdown, notes, insights, messages) now scrolls as one unit instead of cutting off cost breakdown
- **Memory usage** — Preview parser uses streaming readline instead of loading entire JSONL file into memory, capped at 50 sampled messages

## [0.3.1] - 2026-03-01

### Added

- **AI insight indicators** — Purple "AI" badge on session cards shows which sessions have cached insights (summary, megaprompt, insights)
- **Has AI filter** — Filter pill to show only sessions with AI analysis

### Fixed

- **WezTerm resume** — Opens tab in running instance (`cli spawn`) instead of new window, with fallback
- **Cost breakdown overflow** — Formula table scrolls horizontally in narrow sidebar instead of clipping

## [0.3.0] - 2026-03-01

### Added

- **AI Session Insights** — Generate Summary, Megaprompt, and Insights for any session using Claude CLI headless mode, with SQLite caching and staleness detection
- **Model selector** — Choose Opus, Sonnet, or Haiku for insights and refinement generation
- **Prompt Refinement** — Refine any prompt with 6 flavors: Token Efficient, Speed Optimized, Quality Maximized, Structured, Expert Persona, All Combined. Supports multi-flavor selection, recursive refinement, custom instructions, and save-as-prompt
- **Terminal tab support** — Resume sessions in new tabs (instead of windows) for iTerm2, WezTerm, and Kitty
- **New terminals** — Added Ghostty and Windows Terminal support, plus Command Prompt on Windows
- **Eval system** — Rigorous prompt evaluation pipeline: 600 refinements across 30 prompt versions, LLM-as-judge scoring, HTML report with dark/light themes

### Improved

- **Refinement prompts** — All 6 flavor prompts updated with winning strategies from eval (CoT, Meta-prompt, Rubric, Few-shot patterns scored 4.0-4.6 avg by LLM judge)
- **Cross-platform terminals** — Binary detection helpers for macOS, Linux, and Windows

## [0.2.5] - 2026-03-01

### Improved

- **Crisp Retina screenshots** — All screenshots at 2x/144 DPI with explicit `width` attributes for sharp rendering on all displays
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
