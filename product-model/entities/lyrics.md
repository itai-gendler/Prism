---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/lyrics/Lyrics.kt
---

# Lyrics

Lyrics kept for a track and source, with choices and timing adjustments used when presenting them.

## Information kept

- **Text** — Lyric lines and available background vocals.
- **Timing** — Word timings, line timings or plain text.
- **Source** — Provider and saved source choice for this track.
- **Search name** — Optional alternative title and artist for lookup.
- **Offset** — The listener’s saved timing adjustment; video timing may have a separate offset.
- **Translation** — Available translated lines and chosen language.
