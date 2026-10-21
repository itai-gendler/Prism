---
appliesTo:
- type: entity
  id: lyrics
  effect: changes
  facts:
  - Text
  - Timing
  - Source
  - Search name
  - Offset
permits:
- actors:
  - listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/lyrics/Lyrics.kt
---

# The listener's lyric choices for a song stay on the phone

Choosing a source, another search title or a timing for a song needs no YouTube Music account.
