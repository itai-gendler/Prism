---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener presses previous in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product restarts the song or goes back to the one heard before it.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Current
  - entity: playback
    effect: changes
    facts:
    - Media
    - Position
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

# Skip to previous in the car

## Trigger

The listener presses previous in Android's media controls.

## Outcome

The song restarts, or the song heard before it plays.
