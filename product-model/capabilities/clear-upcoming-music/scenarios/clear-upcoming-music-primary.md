---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Clear in the queue.
  kind: actor
  entities:
  - entity: queue
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product takes everything after the current song out of the queue, autoplay's suggestions included.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Order
    - Suggestions
    - Added by listener
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

# Clear what's up next

## Trigger

The listener wants nothing more after the current song.

## Outcome

Everything after the current song leaves the queue; the current song keeps playing.
