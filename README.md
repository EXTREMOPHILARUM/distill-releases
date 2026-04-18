# Distill

Built `.dmg` downloads for **Distill**.

Latest: **[Releases page](https://github.com/EXTREMOPHILARUM/distill-releases/releases)**

## Philosophy

Distill is an AI-native photo manager — not a traditional gallery with a chatbot glued on top. The AI *is* the interface. You tell it what you want ("show me the best group photos", "cull the blurry ones", "export the picks at 4K") and it drives the app through a local MCP server of first-class tools. The chat bubble is the workflow, not a helper.

- **Local-first.** Your photos never leave the machine. Face detection, clustering, scoring, and scene tagging all run on-device; the only network call is to the Claude API for chat, and even that runs over an SDK sidecar you own.
- **Tools over prompts.** ~44 explicit tools — `query_photos`, `compare_photos`, `auto_cull`, `export_photos` — each does one thing well. The AI composes them; it doesn't fake UI by hallucinating.
- **Native performance.** Apple Silicon first. CoreML for face models, `sips` for thumbnails, SQLite WAL for per-project state. No Electron, no cloud roundtrip.
- **Non-destructive by default.** Edits live in an append-only stack. Flags and rejections are reversible. Your RAW files stay untouched on disk.

## Install

1. Download `distill_<version>_aarch64.dmg` (Apple Silicon only).
2. Open the `.dmg` and drag **distill.app** to `/Applications`.
3. Strip the quarantine flag so macOS will run the unsigned build:
   ```sh
   xattr -cr /Applications/distill.app
   ```
   Without this, recent macOS shows **"distill is damaged and can't be opened"**. The right-click → Open workaround doesn't bypass it on macOS 14+.
4. Open **distill.app** from `/Applications`.

Signed + notarized builds land once a Developer ID cert is in place; until then, step 3 is required.
