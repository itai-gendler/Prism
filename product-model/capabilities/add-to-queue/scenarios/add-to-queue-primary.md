---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Add to queue.
  kind: actor
  entities:
  - entity: queue
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product puts the music after the songs already added to the queue and ahead of autoplay's suggestions.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Order
    - Added by listener
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

# Add to queue

## Trigger

The listener wants music to play after what is already queued.

## Outcome

The music waits after the songs already added and ahead of autoplay's suggestions.
