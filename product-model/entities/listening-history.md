---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/db/Database.kt
---

# Listening history

The on-device record used for Replay and listening-based selections.

## Information kept

- **Music** — Track heard.
- **When** — When listening time was recorded.
- **Time heard** — Accumulated playing time retained for the track.
- **Recent music** — Tracks ordered by the last time they began playing.
