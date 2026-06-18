# Releases

Public download mirror for tsengrex's macOS apps. DMGs are attached as GitHub Release assets — see the [Releases](https://github.com/zengxiang0217/releases/releases) tab.

## Typemore

A macOS menu-bar voice dictation tool for "Vibe Coding" — dictate engineering prompts to AI coding assistants (Claude Code, Cursor, etc.). Tap **Right Command** to start/stop recording; the transcript is cleaned by an LLM and pasted at the cursor. First-class support for Chinese, English, and mixed input.

Latest: [Typemore v1.0.1](https://github.com/zengxiang0217/releases/releases/tag/typemore-v1.0.1)

## VoiceBridge

A macOS real-time voice translator. Speak into the mic, the other side hears the translation in their language. Four hot-swappable backends (OpenAI Realtime / Qwen-Omni / Qwen Pipeline / Qwen3-Omni). Mini-mode for face-to-face meetings, archive history with cross-session search + LLM summaries, and full keyboard control. Source: [Ooze](https://github.com/zengxiang0217/Ooze).

Latest: [VoiceBridge v0.91.0](https://github.com/zengxiang0217/releases/releases/tag/voicebridge-v0.91.0)

## Realtime Translator

A macOS menu-bar live-caption + translation overlay. Captures Zoom / system / mic audio, transcribes with Whisper or Apple Speech, translates with GPT or the Realtime API. Floating draggable overlay with click-through, 12 global hotkeys, per-session translation cache, glossary with auto-suggest, WebVTT subtitle export, and one-click "Save meeting notes" that bundles an AI summary with the full transcript. Source: [realtime_translation](https://github.com/zengxiang0217/realtime_translation).

Latest: [Realtime Translator 0.92.0](https://github.com/zengxiang0217/releases/releases/tag/rt-v0.92.0)

---

## First launch — bypassing Gatekeeper

These apps are **not** signed with an Apple Developer ID ($99/yr), so the system will show:

> "AppName" Not Opened — Apple could not verify "AppName" is free of malware …

The old "right-click → Open" trick was closed in macOS 14+. Pick one of two paths:

**Drag the app out of the mounted DMG first** (e.g. into `/Applications`). The DMG mount at `/Volumes/AppName/` is read-only — neither path below works while the app still lives there.

### A. Terminal one-liner (10 seconds)

Strips the quarantine flag downloads carry:

```bash
xattr -dr com.apple.quarantine /Applications/Typemore.app
xattr -dr com.apple.quarantine /Applications/VoiceBridge.app
xattr -dr com.apple.quarantine "/Applications/Realtime Translator.app"
```

Substitute your actual path if you put it somewhere else (`~/Applications`, `~/Desktop`, etc.). Double-click after — it just opens, and never asks again.

### B. System Settings (no terminal)

1. Double-click the app once — let the warning pop up, click Done
2. Open **System Settings → Privacy & Security**
3. Scroll to the Security section — there's a line `"AppName" was blocked …` with an **Open Anyway** button
4. Click Open Anyway → enter password → double-click the app again — this time the dialog has an Open option

Both are one-time per app. Once done, Gatekeeper stops bothering you about that app.
