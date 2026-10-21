---
kind: primary
routes:
  main: Main path
steps:
- text: The listener removes a song from the playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product takes the song off the list and removes it in the YouTube Music account, restoring the list if that fails.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Tracks
  - entity: song
    effect: reads
    facts: []
  - entity: account
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Remove a song from a playlist

## Trigger

The listener takes a song out of one of their own playlists.

## Outcome

The song leaves the playlist; if YouTube Music refuses, the song is shown again.
