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
- entity: album
  shows:
  - Title
  - Artists
  - Release
  - Tracks
  - Artwork
  - Saved
- entity: artist
  shows:
  - Name
  - Artwork
  - Sections
  - Favourite
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
  - Recent searches
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SearchScreen.kt
---

# Search

Search: results as you type across songs, albums, artists, playlists and videos, recent searches, and a search of music on the phone.
