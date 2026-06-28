# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.4`

Update URL:

```text
https://raw.githubusercontent.com/nupa0w0-hash/supervibebot-update/main/SuperVibeBot.update.js
```

Files:

- `SuperVibeBot.update.js`: RisuAI auto-update target
- `SuperVibeBot.js`: same build, plain filename
- `SuperVibeBot.auto.js`: same build, install alias

This repository is dedicated to SuperVibeBot only. Other plugins should use their own update repositories to avoid release and cache conflicts.

## 1.5.4

- Adds adaptive runtime limits for PocketRisu, mobile webviews, low-memory devices, and background tabs.
- Keeps sub-agent packet size below the effective context budget with extra headroom.
- Reduces sub-agent parallelism, manager-board size, workstream render count, and bulk-create chunk size on constrained devices.
- Debounces workstream rendering and flushes state on visibility changes to reduce webview crashes.
- Adds runtime diagnostics for adaptive mobile/PocketRisu budgets.

## 1.5.3

- Adds sub-agent payload budgeting to reduce browser/webview memory spikes.
- Dynamically limits sub-agent parallel calls for large context payloads.
- Caps workstream details and sub-agent manager board size.
- Avoids rebuilding full module/plugin work target context while rendering the workstream panel.
