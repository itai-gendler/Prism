---
entities:
- entity: listening-history
  shows:
  - Music
  - When
  - Time heard
  - Recent music
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ReplayScreen.kt
---

# Replay

Replay: listening minutes, top songs, artists and genres for a chosen period, with Play, Shuffle, the Replay story and sharing.
