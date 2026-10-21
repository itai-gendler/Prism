---
appliesTo:
- type: entity
  id: episode
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/EpisodeProgress.kt
---

# Episode progress is separate from music Replay

Progress starts being retained at thirty seconds. Within a minute of a known ending the episode is marked played; at most fifty unfinished entries are kept and finished episodes start from the beginning when played again.
