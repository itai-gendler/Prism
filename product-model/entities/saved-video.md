---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt
---

# Saved video

An offline music video kept alongside an audio download.

## Information kept

- **Track** — The song and the resolved video.
- **Progress** — Aggregate progress and bytes for the picture and required audio.
- **Status** — Queued, downloading, completed or failed.
