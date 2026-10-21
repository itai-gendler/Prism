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
- entity: preferences
  shows:
  - Home
  - Pinned playlists
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/HomeScreen.kt
---

# Home

Home: the catalog shelves for this listener, Quick picks, Speed dial, shortcuts and pinned playlists.
