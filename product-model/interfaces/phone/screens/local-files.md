---
entities:
- entity: music-file
  shows:
  - Tags
  - Format
  - Added
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
- entity: preferences
  shows:
  - Local sections
  - Music access
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LocalMusicScreen.kt
---

# Local files

Local files: the music files already on the phone, by song, album or artist, with the sections the listener chose.
