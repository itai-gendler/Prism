---
kind: primary
routes:
  main: Main path
steps:
- text: The listener unpins a playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::home
- text: The Product removes the playlist from the pinned playlists on Home.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Pinned playlists
  - entity: playlist
    effect: reads
    facts:
    - Title
  actor: listener
  contexts:
    main:
      place: phone::home
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CatalogueScreen.kt#PinPlaylistsSheet
---

# Unpin a playlist from Home

## Trigger

The listener no longer wants a playlist pinned on Home.

## Outcome

The playlist leaves the pinned playlists on Home.
