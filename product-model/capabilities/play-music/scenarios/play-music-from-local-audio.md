---
kind: alternate
routes:
  main: Android app
steps:
- text: The listener plays a saved collection while offline.
  kind: actor
  entities: []
  contexts:
    main:
      place: phone::album
  actor: listener
- text: The Product queues only the songs available offline and starts from the chosen one.
  kind: product
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Source
  - entity: playback
    effect: changes
    facts:
    - Media
    - Position
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::album
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Play a collection offline

## Trigger

The listener plays an album or playlist while offline.

## Outcome

Only the collection's songs that can play offline are queued, starting from the chosen one.
