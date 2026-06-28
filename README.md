# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.7`

Update URL:

```text
https://raw.githubusercontent.com/nupa0w0-hash/supervibebot-update/main/SuperVibeBot.update.js
```

Files:

- `SuperVibeBot.update.js`: RisuAI auto-update target
- `SuperVibeBot.js`: same build, plain filename
- `SuperVibeBot.auto.js`: same build, install alias

This repository is dedicated to SuperVibeBot only. Other plugins should use their own update repositories to avoid release and cache conflicts.

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

## 1.5.5

- Prevents desktop RisuAI web from being downgraded to low tier solely because `navigator.deviceMemory` reports 4GB.
- Keeps a protection path for genuinely constrained 4GB desktops when low core count, low heap limit, or high heap usage is also detected.
- Keeps mobile, webview, and PocketRisu low-memory protections by applying the 4GB, low-core, and network-saving heuristics to mobile-like runtimes.
- Hardens workstream rendering so background skips, render failures, and stale async completions do not drop pending updates.

## 1.5.4

- Adds adaptive runtime limits for PocketRisu, mobile webviews, low-memory devices, and background tabs.
- Keeps sub-agent packet size below the effective context budget with extra headroom.
- Reduces sub-agent parallelism, manager-board size, workstream render count, and bulk-create chunk size on constrained devices.
- Debounces workstream rendering and flushes state on visibility changes to reduce webview crashes.

## 1.5.3

- Adds sub-agent payload budgeting to reduce browser/webview memory spikes.
- Dynamically limits sub-agent parallel calls for large context payloads.
- Caps workstream details and sub-agent manager board size.
- Avoids rebuilding full module/plugin work target context while rendering the workstream panel.