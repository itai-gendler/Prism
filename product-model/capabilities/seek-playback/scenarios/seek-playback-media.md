---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener seeks in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product moves playback to that position.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Position
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Seek in the car or from the notification

## Trigger

The listener seeks from Android's media controls.

## Outcome

Playback moves to the new position.
