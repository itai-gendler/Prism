---
appliesTo:
- type: entity
  id: lyrics
  effect: changes
  facts:
  - Translation
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt
permits:
- actors:
  - listener
  when:
  - entity: preferences
    fact: Translate lyrics
    is: true
---

# Lyrics are translated only when the listener turns translation on

Only the lyric text is sent to Google Translate; when no usable translation comes back, the original lyrics stay.
