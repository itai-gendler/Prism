---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/EpisodeProgress.kt
---

# Episode

A podcast episode with its own on-device listening progress.

## Information kept

- **Title** — Episode name and show.
- **Details** — Description, publication information, artwork and duration when available.
- **Position** — Saved listening position.
- **Last heard** — When progress was last saved.

## States

### Unplayed

No completed-listening marker.

### In progress

A meaningful unfinished position is retained.

### Played

Marked completed manually or near its end.
