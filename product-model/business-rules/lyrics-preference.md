---
appliesTo:
- type: entity
  id: lyrics
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/lyrics/Lyrics.kt#auto
---

# A saved source choice takes priority in normal lyric loading

For normal automatic loading, a usable per-song chosen source wins. Otherwise saved and enabled provider results follow the configured order and preference: word timing, then line timing, then plain text when timing preference is enabled.
