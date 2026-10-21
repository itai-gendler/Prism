---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener opens a playlist Prism has saved while there is no usable network.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product shows the playlist's last saved details and tracks.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Offline copy
    - Tracks
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Open a saved playlist offline

## Trigger

The phone has no usable network.

## Outcome

The playlist shows the details and tracks Prism last saved; which tracks can play is decided separately.
