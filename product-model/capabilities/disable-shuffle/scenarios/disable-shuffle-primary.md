---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns shuffle off.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product turns shuffle off and plays the queue in its own order.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Shuffle
    - Order
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Turn shuffle off

## Trigger

The queue is shuffled.

## Outcome

The queue plays in its own order again.
