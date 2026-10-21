---
entities:
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
- entity: playlist
  shows:
  - Title
  - Picture
  - Tracks
- entity: album
  shows:
  - Title
  - Artists
  - Artwork
  - Tracks
- entity: listening-history
  shows:
  - Recent music
- entity: download
  shows:
  - Track
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/MediaTree.kt
---

# Music browser

The music lists Prism offers to Android Auto and other media browsers: Home, Liked songs, the library, Downloads and recent plays, and search results.
