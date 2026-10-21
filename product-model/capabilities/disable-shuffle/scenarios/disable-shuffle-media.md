---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener turns shuffle off in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
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
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Turn shuffle off in the car

## Trigger

The listener uses the shuffle button on the car's player.

## Outcome

The queue plays in its own order again.
