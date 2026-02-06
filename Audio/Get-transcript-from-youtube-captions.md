# Get Transcript from YouTube Captions (CC)

When a video already has captions (manual or auto-generated), you can download them and convert to plain text without doing any speech-to-text.

## Option A: `yt-dlp` (recommended)

### 1) Download captions only (no video)

```bash
# Auto-captions (most common)
yt-dlp --skip-download --write-auto-sub --sub-lang "en.*" \
  --convert-subs vtt -o "%(title)s.%(ext)s" "<YOUTUBE_URL>"

# If you want human-made subtitles instead of auto:
yt-dlp --skip-download --write-sub --sub-lang "en.*" \
  --convert-subs vtt -o "%(title)s.%(ext)s" "<YOUTUBE_URL>"
```

This produces a `.vtt` file (WebVTT).

### 2) Convert `.vtt` → plain text

```bash
# macOS / Linux
sed -E 's/<[^>]+>//g' *.vtt | grep -vE '^(WEBVTT|NOTE|[0-9]{2}:[0-9]{2}:[0-9]{2}\.)' \
  | sed '/^$/d' > transcript.txt
```

If the output contains duplicated lines (common in auto-captions), a simple de-dup pass can help:

```bash
awk 'NF && $0!=prev {print} {prev=$0}' transcript.txt > transcript.dedup.txt
```

## Option B: Copy from YouTube UI

If the UI shows “Show transcript”, you can copy-paste it directly. This is fast, but harder to automate and may lose punctuation/formatting.

## Notes / Caveats

- Some videos have no captions at all; in that case use audio transcription (e.g. Whisper).
- Captions are language-specific; adjust `--sub-lang` (e.g. `zh-Hans`, `zh`, `ja`, `ko`).
- Respect YouTube’s Terms of Service and local laws when downloading content.

