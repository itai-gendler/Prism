---
kind: primary
routes:
  main: Main path
steps:
- text: The listener enters a name and visibility.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::library
- text: The Product makes the playlist in the YouTube Music account and refreshes the library.
  kind: product
  entities:
  - entity: playlist
    effect: creates
    facts:
    - Title
    - Visibility
    - Owned
  - entity: account
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::library
- text: The Product opens the new playlist.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Visibility
    - Tracks
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerQueue.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LikedPlaylist.kt
---

# Create a playlist and open it

## Trigger

The listener starts a new playlist in Library.

## Outcome

The new playlist exists in the YouTube Music account and opens, ready to fill.
