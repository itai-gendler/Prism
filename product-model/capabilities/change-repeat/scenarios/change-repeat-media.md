---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener uses the repeat button in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product changes repeat.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Repeat
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Change repeat in the car

## Trigger

The listener uses the repeat button on the car's player.

## Outcome

Repeat moves to its next choice.
