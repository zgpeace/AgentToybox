# Transcribe YouTube Audio to Text (Whisper)

Use this when a YouTube video has **no captions**, or you need higher-quality transcripts than auto-captions.

## 1) Download audio with `yt-dlp`

```bash
# Best-quality audio → .m4a (or webm/opus depending on source)
yt-dlp -f "ba" -o "audio.%(ext)s" "<YOUTUBE_URL>"
```

If you prefer a consistent format, convert to WAV (good for some tools, but bigger):

```bash
ffmpeg -i audio.* -ar 16000 -ac 1 audio.wav
```

## 2) Transcribe with Whisper (Python CLI)

Install:

```bash
python -m pip install -U openai-whisper
```

Run:

```bash
whisper audio.* --model medium --language en --task transcribe \
  --output_format txt --output_dir .
```

Outputs a `.txt` (and optionally `.srt/.vtt/.json` depending on flags).

## Alternative: `whisper.cpp` (fast, local)

If you prefer a lighter, C++ implementation (often faster on Apple Silicon), use `whisper.cpp` and run its `main`/`whisper-cli` against `audio.wav`. Exact install/build steps depend on your platform.

## Notes / Caveats

- Whisper models: `tiny`/`base` are fast; `small`/`medium` balance; `large` is best quality but slow.
- For long videos, split audio into chunks (e.g. 10–30 min) to improve reliability and resume on failures.
- Always comply with YouTube’s Terms of Service and local laws when downloading and processing content.

