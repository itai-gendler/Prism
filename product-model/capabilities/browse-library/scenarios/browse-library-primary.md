---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Library.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::library
- text: The Product lists liked songs, playlists, albums and artists.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Description
    - Visibility
    - Tracks
    - Owned
    - Saved
    - Picture
    - Offline copy
  - entity: album
    effect: reads
    facts:
    - Title
    - Artists
    - Release
    - Tracks
    - Artwork
    - Saved
    - Offline copy
  - entity: artist
    effect: reads
    facts:
    - Name
    - Artwork
    - Sections
    - Favourite
    - Channel
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Duration
    - Artwork
    - Source
    - Liked
    - Not for me
    - Last played
  - entity: account
    effect: reads
    facts:
    - Signed in
    - Identity
    - Library sync
    - Liked playlist
  actor: listener
  contexts:
    main:
      place: phone::library
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
---

# Browse the library

## Trigger

The listener opens Library.

## Outcome

Liked songs, playlists, albums and artists are listed, favourite artists first.
