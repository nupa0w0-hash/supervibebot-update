# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.11`

Update URL:

```text
https://raw.githubusercontent.com/nupa0w0-hash/supervibebot-update/refs/heads/main/SuperVibeBot.update.js
```

Files:

- `SuperVibeBot.update.js`: RisuAI auto-update target
- `SuperVibeBot.js`: same build, plain filename
- `SuperVibeBot.auto.js`: same build, install alias

This repository is dedicated to SuperVibeBot only. Other plugins should use their own update repositories to avoid release and cache conflicts.

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
