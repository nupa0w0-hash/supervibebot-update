# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.8`

Update URL:

```text
https://raw.githubusercontent.com/nupa0w0-hash/supervibebot-update/main/SuperVibeBot.update.js
```

Files:

- `SuperVibeBot.update.js`: RisuAI auto-update target
- `SuperVibeBot.js`: same build, plain filename
- `SuperVibeBot.auto.js`: same build, install alias

This repository is dedicated to SuperVibeBot only. Other plugins should use their own update repositories to avoid release and cache conflicts.

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