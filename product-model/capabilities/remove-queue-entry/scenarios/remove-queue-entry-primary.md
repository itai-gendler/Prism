---
kind: primary
routes:
  main: Main path
steps:
- text: The listener removes a song from the queue.
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
- text: The Product takes the song out of the queue.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Order
    - Suggestions
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

# Remove a song from the queue

## Trigger

The listener does not want a queued song.

## Outcome

The song leaves the queue.
