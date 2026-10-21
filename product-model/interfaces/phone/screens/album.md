---
entities:
- entity: album
  shows:
  - Title
  - Artists
  - Release
  - Tracks
  - Artwork
  - Saved
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
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Album

One album: its release details and tracks, with play and shuffle, and saving it to or removing it from the library.
