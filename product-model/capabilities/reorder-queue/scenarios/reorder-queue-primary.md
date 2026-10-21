---
kind: primary
routes:
  main: Main path
steps:
- text: The listener drags a song to a new place in the queue.
  kind: actor
  entities:
  - entity: queue
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product moves the song to that place.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Order
    - Manual arrangement
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerQueue.kt
---

# Reorder the queue

## Trigger

Shuffle is off and the listener wants a queued song elsewhere.

## Outcome

The song plays at its new place in the queue.
