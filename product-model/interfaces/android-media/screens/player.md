---
entities:
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
- entity: playback
  shows:
  - Position
  - Media
  - Error
- entity: queue
  shows:
  - Entries
  - Current
  - Shuffle
  - Repeat
- entity: lyrics
  shows:
  - Text
  - Timing
- entity: preferences
  shows:
  - Car lyrics
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# Media player

The car's or Android's player for what Prism is playing: the song and its progress, and the controls Prism offers, including like, shuffle, repeat, car lyrics, start radio and Not for me.
