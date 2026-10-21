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
  - Visibility
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
- entity: preferences
  shows:
  - Library
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
---

# Library

Library: liked songs, playlists, albums and artists, local files, and creating or ordering playlists.
