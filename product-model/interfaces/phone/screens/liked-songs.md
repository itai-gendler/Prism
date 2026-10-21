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
- entity: playlist
  shows:
  - Title
  - Description
  - Visibility
  - Tracks
  - Picture
  - Saved
- entity: account
  shows:
  - Signed in
  - Identity
  - Library sync
  - Liked playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LikedPlaylistSheet.kt
---

# Liked songs

Liked songs, with the Liked songs playlist Prism can keep up to date in the YouTube Music account.
