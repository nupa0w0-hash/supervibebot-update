# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.22`

Update URL:

```text
https://github.com/nupa0w0-hash/supervibebot-update/releases/latest/download/SuperVibeBot.update.js
```

Files:

- `SuperVibeBot.update.js`: RisuAI auto-update target
- `SuperVibeBot.js`: same build, plain filename
- `SuperVibeBot.auto.js`: same build, install alias

This repository is dedicated to SuperVibeBot only. Other plugins should use their own update repositories to avoid release and cache conflicts.

## 1.5.22

- Removes source/raw-like Korean wording from plugin `//@update-url` guidance.
- Uses "HTTPS .js file URL" wording in validation messages so authors do not confuse it with GitHub raw branch URLs.
- Keeps the GitHub Releases `latest/download` recommendation from 1.5.21.

## 1.5.21

- Updates Kero's RisuAI plugin creation guidance to prefer GitHub Releases `latest/download` update URLs.
- Stops recommending GitHub raw branch URLs as default auto-update channels because they can cache stale plugin files.
- Keeps the 1.5.20 runtime update URL guard intact.

## 1.5.20

- Adds a runtime diagnostic guard for SuperVibeBot's own update URL.
- Verifies that the official update URL uses the GitHub Releases `latest/download` asset path.
- Fails diagnostics if the update URL regresses to the raw refs paths that caused cache/update problems.

## 1.5.19

- Adds a runtime diagnostic self-test for the legacy field policy introduced in 1.5.18.
- Verifies that AI-generated lorebook writes suppress `secondkey` and `mode:"multiple"` unless explicitly requested.
- Verifies that model context hides legacy lorebook activation details and character `personality/scenario` aliases.

## 1.5.18

- Keeps existing lorebooks compatible while stopping new AI-generated writes from defaulting to `secondkey` or `mode:"multiple"`.
- Scrubs legacy lorebook activation details from model context so Kero and sub-agents do not copy them back by habit.
- Filters character `personality/scenario` alias fields out of raw extra model context.
- Updates NPC lore wording from legacy `Personality` labels to `Traits/Behavior`.

## 1.5.17

- Moves the primary update URL to the GitHub Releases `latest/download` asset path to avoid raw branch-cache delays.
- Keeps the 1.5.16 compatibility bridge for installs that already received the bad 1.5.14 raw URL.

## 1.5.16

- Uses the `github.com/.../raw/refs/heads/main/...` update URL form because it fetches the latest branch file reliably.
- Adds a compatibility bridge path for installs that already received the bad 1.5.14 raw.githubusercontent `refs/heads/main` update URL.

## 1.5.15

- Fixes the update metadata URL to the GitHub raw `/main/` path that RisuAI can fetch.
- Keeps the 1.5.14 PocketRisu/WebView stability fixes intact.

## 1.5.14

- Caps sub-agent consultation packets to 120k desktop, 80k constrained, and 60k background chars.
- Releases Kero chat task locks if resume/setup storage operations fail before the main protected run.
- Applies lorebook/regex/trigger `idx` filters instead of relying on whichever current result is open.
- Coalesces background status DOM rendering to reduce PocketRisu/WebView progress-update pressure.
- Treats lorebook multiple keys and `secondkey` as explicit advanced options, not defaults.

## 1.5.13

- Adds hard upper bounds to explicit sub-agent output overrides so WebView-safe limits cannot be bypassed accidentally.
- Truncates oversized sub-agent responses before JSON parsing and manager-board rendering if a provider ignores `max_tokens`.
- Forces sub-agent parallelism to 1 for payloads over 120k serialized characters, even if WebView/mobile detection misses the runtime.
- Adds runtime diagnostics for hard output caps and response-character truncation.

## 1.5.12

- Adds a separate output-token cap for sub-agent manager reports: 4096 on normal desktop profiles and 2048 on constrained/mobile/webview profiles.
- Reduces WebView/PocketRisu crash pressure when GLM/Kimi/API Hub sub-agents return oversized reports.
- Keeps explicit `subAgentMaxOutputTokens` overrides available for advanced cases.
- Adds runtime diagnostics for sub-agent output caps.

## 1.5.11

- Fixes the missing-action path for lorebook/regex/trigger improve requests so Kero does not only talk and then fail to save when the model omitted `@action`.
- Unqualified part edits now target checked items or the currently open item instead of silently expanding to every item.
- Explicit all/every/전체 requests still run as all-item jobs.
- Blocks malformed embedded `@action` text before it can be saved into character fields or lorebook content.
- Adds runtime self-checks for lorebook fallback, selected-item expansion, and malformed embedded action recovery.

## 1.5.10

- Reduces PocketRisu/WebView crash pressure during sub-agent work by making heartbeat-like workstream progress events in-memory only instead of persisting every progress tick.
- Prunes stored action jobs and bulk-create jobs before pluginStorage writes, preserving active jobs while compacting/expiring completed job details.
- Caps the runtime queued-input list as well as the persisted queue so long tasks cannot grow the queue UI indefinitely.
- Reuses and throttles foreground status toasts so progress updates do not append many DOM nodes/timers at once.
- Expands mobile/tablet/coarse-pointer detection so constrained devices more reliably use one sub-agent at a time.

## 1.5.9

- Changes the metadata `//@update-url` to the `refs/heads/main` raw URL form so the auto-update channel is less exposed to stale GitHub raw branch-path cache.
- Keeps the 1.5.8 queue/abort stability fixes intact.

## 1.5.8

- Passes abort signals through `pluginFetchJson` for RisuAI `risuFetch` paths as well as native/browser fetch paths, reducing late API Hub/Ollama sub-agent work after hard timeouts.
- Adds a runtime diagnostic self-test for plugin fetch abort signal routing.
- Fixes a queued-input drain gap: if a user adds another follow-up while the queue is already draining, SuperVibeBot now schedules one more drain pass after the current snapshot finishes.
- Adds a runtime diagnostic self-test for the queued-input re-drain policy.

## 1.5.7

- Removes an older duplicated top-level LBI/Ollama/API Hub helper block so strict parsers and webviews do not trip over duplicate declarations.
- Keeps the newer API Hub/sub-agent implementation as the single active implementation.
- Removes the remaining duplicated `ensureArray` helper and verifies `no-redeclare` / `no-undef` for the release file.
- Rebuilds the release from the clean UTF-8 1.5.6 source to avoid Korean text corruption.

## 1.5.6

- Registers safe local runtime output/render ops before wake recovery so restored missions can show their recovery notice immediately.
- Keeps action execution, queue draining, and bulk job execution registered after assistant state initialization to avoid pre-init mutation.
- Adds a shared selected-index fallback helper so checked lorebook/regex/trigger actions keep the intended item index.
- Adds a runtime diagnostic self-test for explicit and fallback selected indexes.
