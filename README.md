# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.56`

Update URL:

```text
https://raw.githubusercontent.com/nupa0w0-hash/supervibebot-update/refs/heads/main/SuperVibeBot.update.js
```

Files:

- `SuperVibeBot.update.js`: RisuAI auto-update target
- `SuperVibeBot.js`: same build, plain filename
- `SuperVibeBot.auto.js`: same build, install alias

This repository is dedicated to SuperVibeBot only. Other plugins should use their own update repositories to avoid release and cache conflicts.

## 1.5.56

- Switches the auto-update URL to `raw.githubusercontent.com/.../refs/heads/main/...` so fresh releases are not hidden by the stale `/main/` raw cache.

## 1.5.55

- Removes bulk-create character-budget chunk shrinking so rich lorebook jobs start with multi-item chunks.
- Uses enabled sub-agents by default in work-mode bulk, recovery, and chunk generation paths.
- Carries existing and job-local lorebook identities into chunk prompts to avoid repeating the same title with slightly changed text.

## 1.5.54

- Removes local duplicate/fingerprint gates from lorebook, regex, trigger, and character patch append saves.
- Stops pruning stored action jobs, bulk jobs, and bulk edit state by local expiration time.

## 1.5.53

- Raises auto/unknown/router model output fallbacks to 128K instead of silently falling back to 8192.
- Keeps enabled sub-agents parallel across bulk chunks instead of shrinking to one worker on large/mobile payloads.
- Removes fixed 50/1000 bulk-count behavior and preserves requested counts for resume.
- Removes the local short-content quality gate so the LLM output is not rejected just because local heuristics dislike the length.

## 1.5.52

- Removes 8K hard caps from Kero preplan/recovery calls so model-specific output budgets are used.
- Treats bulk-create item limits as split budgets instead of content-shrink caps, allowing rich lorebook entries to use larger model budgets and more calls.
- Prevents "no summary / 요약 없이" from being misread as compression and preserves explicit sub-agent requests into bulk chunk generation.

## 1.5.51

- Treats delegated requests such as "알아서", "최종완료", and "끝까지" as execution authorization instead of asking for preference confirmation.
- Replaces loose bulk-count parsing so numbered lists are not mistaken for lorebook counts.
- Sends missing, clarification-only, or underfilled full-build responses back through LLM action recovery before any local chunk-queue fallback.

## 1.5.50

- Removes local character/world generation fallback so local code cannot invent names, descriptions, first messages, HTML, or starter lorebooks.
- Converts large remake/empty-bot recovery into LLM bulk-create chunk queues only, preserving reference digests without embedded world anchors.
- Disables local image asset prompt fallback so image prompts must come from the LLM action or Asset Studio controls.

## 1.5.49

- Prevents local large-request preplanning from overwriting characters with canned fallback worlds.
- Uses a compact model-assisted first chunk for remake/empty-bot jobs before queuing bulk-create follow-up work.
- Removes fallback world anchors from safe bulk-create preplan requests.

## 1.5.48

- Routes broad remake/rebuild/empty-bot project requests into immediate character patch and chunked bulk-create execution.
- Carries compact reference character/module/plugin digests into preplanned jobs so large reference-heavy work does not ask the user to restate the task.
- Treats short follow-ups such as "start", "do it", or "go" as execution of the previous mission objective.
- Keeps explicit single-field edits protected from accidental full-character rebuild escalation.

## 1.5.47

- Adds a "복합 작업" checkbox to the work-target/reference selection dialog.
- Allows checked reference characters, modules, and plugins to be writable only when the checkbox is on.
- Blocks mixed write actions whose character id, module id, or plugin name is not the current target or a checked reference target.

## 1.5.36

- Adds Asset Studio quick-start controls for Wellspring selection, default preset recovery, and common emotion/standing image presets.
- Shows the active image profile and preset summary before generation.
- Prompts for a missing Wellspring ws-key from Asset Studio when enabling Wellspring.

## 1.5.35

- Adds a Wellspring NAI image provider preset for `https://wellspring.encrypt.gay/v1/images/nai/generate-image`.
- Adds a one-click `Wellspring 추가` image API profile and ws-key/profile connection check.
- Treats Wellspring NAI and generic NAI presets as compatible in Asset Studio generation.

## 1.5.34

- Adds Kero's "수정 전 확인" toggle, deferring save actions to the approve/reject proposal panel when enabled.
- Stops usage/question/analysis requests from being converted into lorebook, regex, or trigger save actions.
- Parses `module_update`-style action aliases while rejecting module updates contaminated with character-only fields.
- Recovers clear module trigger line-removal requests, such as `gse-route-label`, as module-only updates.

## 1.5.33

- Preplans obvious large character build requests into a character patch and chunked bulk actions before calling the main model.
- Prevents one-shot NanoGPT calls for requests that already imply full bot/world/roster construction.

## 1.5.32

- Routes NanoGPT/transport timeouts on large character build requests into small-step recovery instead of retrying the same prompt 3 times.
- Keeps short ordinary requests on the normal retry path.

## 1.5.31

- Blocks character fallback/actions while editing module/plugin targets, preventing accidental character overwrite from recovery flows.
- Suppresses completed-only recovery notices and clears mission/action/bulk recovery state when Kero chat is cleared.
- Stabilizes the memory tool drawer height after memory deletion.

## 1.5.30

- Switches the plugin `//@update-url` to the RisuAI-compatible raw main URL.
- Fixes browser/RisuAI Web update checks that can fail on GitHub Releases `latest/download` redirects because RisuAI fetches only `Range: bytes=0-512`.
- Updates plugin creation guidance to prefer `raw.githubusercontent.com` main JS URLs for RisuAI auto-update.

## 1.5.29

- Fixes Kero's mounted chat action parser so `personality`, `scenario`, `성격`, and `시나리오` actions apply through `desc` instead of unused legacy fields.
- Adds diagnostics for the mounted Kero parser path, not just the outer helper path.
- Stops recoverable gateway/hard-timeout failures from retrying the same large original request after recovery fails.
- Saves large lorebook/regex/trigger create payloads in safe chunks and fixes completed bulk summary success counts.

## 1.5.28

- Strengthens Kero chat continuity with stable message ids, read-merge-write chat storage, and target-first global history merging.
- Prevents invalid locale timestamps from being treated as the newest recent chat turn.
- Routes legacy `personality/scenario/성격/시나리오` targets into `desc` and strips legacy lorebook activation fields from AI write paths.
- Makes daily mode use the same safe recent-conversation continuity block as work mode.

## 1.5.27

- Skips automatic sub-agent pre-consultation on PocketRisu/WebView/background runtimes unless the user explicitly asks for sub-agents, GLM, or Kimi.
- Keeps explicit sub-agent requests working, but caps constrained runtime waits to 90 seconds and background waits to 60 seconds.
- Adds runtime diagnostics for the auto-skip and constrained timeout policy.

## 1.5.26

- Tightens practical lorebook defaults: one representative `key` per entry, with aliases kept in content unless explicitly requested.
- Normalizes model-only `keys`/`keyVariants` arrays into a single primary `key` before AI writes are saved.
- Strips `secondaryKey`/`secondkey`/multiple-key variants by default and keeps `personality/scenario` routed into `desc`.

## 1.5.25

- Stops control-only `continue`/`retry` from re-calling the original large prompt when an interrupted mission has no saved actions, bulk jobs, or queued work.
- Reports “no saved work to resume” for empty restored missions instead of entering a repeated timeout/output-limit loop.
- Keeps users on a clear recovery path: either resume saved work or start a new explicit request.

## 1.5.24

- Flushes expired sub-agent consultation guards when runtime diagnostics run.
- Helps recover PocketRisu/WebView sessions where background timer callbacks were delayed while a sub-agent was waiting.
- Makes stuck sub-agent diagnostics judge the post-cleanup state instead of only reporting stale expired guards.

## 1.5.23

- Strengthens runtime diagnostics for unused legacy character fields.
- Verifies full character context does not leak deprecated `personality/scenario` fields or aliases into Kero/sub-agent work context.
- Keeps new traits, behavior, and setup work routed into `desc` instead of old compatibility fields.

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

- Added a separate output-token cap for sub-agent manager reports at the time; the fixed cap was later removed by the model-scale output policy.
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
