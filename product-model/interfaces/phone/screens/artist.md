---
entities:
- entity: artist
  shows:
  - Name
  - Artwork
  - Sections
  - Favourite
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
- entity: album
  shows:
  - Title
  - Artists
  - Release
  - Tracks
  - Artwork
  - Saved
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ArtistScreen.kt
---

# Artist

One artist: picture, information, songs, releases, videos and similar artists, with the listener's favourite choice.
