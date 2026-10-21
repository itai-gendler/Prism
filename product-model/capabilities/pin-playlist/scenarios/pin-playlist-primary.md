---
kind: primary
routes:
  main: Main path
steps:
- text: The listener pins a playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::home
- text: The Product adds the playlist to the pinned playlists on Home.
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
    - Picture
  actor: listener
  contexts:
    main:
      place: phone::home
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CatalogueScreen.kt#PinPlaylistsSheet
---

# Pin a playlist to Home

## Trigger

The listener wants a playlist at hand on Home.

## Outcome

The playlist appears among the pinned playlists on Home.
