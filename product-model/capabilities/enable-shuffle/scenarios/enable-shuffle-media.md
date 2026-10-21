---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener turns shuffle on in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product turns shuffle on with a fresh order that starts from the current song.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Shuffle
    - Order
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Turn shuffle on in the car

## Trigger

The listener uses the shuffle button on the car's player.

## Outcome

The rest of the queue plays in a fresh random order after the current song.
