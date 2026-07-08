# SuperVibeBot Update Channel

SuperVibeBot for RisuAI.

Latest version: `1.5.101`

## Official Update URL

There is exactly one canonical RisuAI auto-update URL:

```text
https://raw.githubusercontent.com/nupa0w0-hash/supervibebot-update/refs/heads/main/SuperVibeBot.js
```

Do not change `//@update-url` to any other host, file, redirect, or alias unless the repository itself is moved and the new channel is verified end to end.

## File Roles

- `SuperVibeBot.js`: canonical auto-update target. This is the only URL that belongs in `//@update-url`.
- `SuperVibeBot.update.js`: byte-identical compatibility copy for old manual/release imports only. It is not the canonical update URL.
- `SuperVibeBot.auto.js`: byte-identical install alias only. It is not the canonical update URL.

All three tracked JavaScript files must stay byte-identical after release generation.

## Forbidden Auto-Update Channels

These must not be used in `//@update-url`:

- GitHub Releases `latest/download` URLs.
- Versioned GitHub release asset URLs.
- `github.com/.../raw/...` compatibility URLs.
- `raw.githubusercontent.com/.../main/...` short raw URLs.
- jsDelivr or other CDN mirrors.
- `SuperVibeBot.update.js` or `SuperVibeBot.auto.js` alias files.

Release assets may still exist for direct import and recovery, but the plugin metadata must always point back to the official `SuperVibeBot.js` raw main URL above.

## Release Checklist

1. Bump `//@display-name`, `//@version`, alert text, diagnostics, and release notes in `SuperVibeBot.js`.
2. Keep `SUPER_VIBE_BOT_CANONICAL_UPDATE_URL` and `SUPER_VIBE_BOT_UPDATE_URL` pointed at the official URL.
3. Copy `SuperVibeBot.js` byte-for-byte to `SuperVibeBot.update.js` and `SuperVibeBot.auto.js`.
4. Run syntax checks on all tracked JavaScript files.
5. Verify that all tracked JavaScript files contain the same `//@update-url`.
6. Push `main`, create the version tag, publish release assets, and run `verify-update-channel.yml`.

The update channel policy is intentionally boring: one official URL, one canonical file, no automatic channel switching.
