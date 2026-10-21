---
entities:
- entity: account
  shows:
  - Signed in
  - Identity
  - Library sync
  - Liked playlist
- entity: playlist
  shows:
  - Title
  - Description
  - Visibility
  - Tracks
  - Picture
  - Saved
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ImportScreen.kt
---

# Import playlist

Import playlists: choose where playlists come from before the transfer continues on the separate transfer service.
