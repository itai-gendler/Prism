---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener presses next in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product moves to the next song.
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

# Skip to next in the car

## Trigger

The listener presses next in Android's media controls.

## Outcome

The next song in play order starts.
