---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens a playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product shows the playlist's details and tracks.
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
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Browse a playlist

## Trigger

The listener opens a playlist.

## Outcome

The playlist's details and tracks are shown and can be sorted or filtered by genre.
