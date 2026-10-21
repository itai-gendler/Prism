---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener opens an album Prism has saved while there is no usable network.
  kind: actor
  entities:
  - entity: album
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
- text: The Product shows the album's last saved details and tracks.
  kind: product
  entities:
  - entity: album
    effect: reads
    facts:
    - Offline copy
    - Tracks
  actor: listener
  contexts:
    main:
      place: phone::album
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Open a saved album offline

## Trigger

The phone has no usable network.

## Outcome

The album shows the details and tracks Prism last saved; which tracks can play is decided separately.
