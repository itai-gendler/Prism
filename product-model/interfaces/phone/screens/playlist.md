---
entities:
- entity: playlist
  shows:
  - Title
  - Description
  - Visibility
  - Tracks
  - Picture
  - Saved
  collects:
  - Title
  - Description
  - Visibility
  - Picture
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
- entity: account
  shows:
  - Signed in
  - Identity
  - Library sync
  - Liked playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Playlist

One playlist: its details and tracks with sorting and genre filters, and, for the listener's own playlists, editing, removing songs and deleting.
