---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener pauses in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product pauses playback where it is.
  kind: product
  entities:
  - entity: playback
    effect: changes
    from: Playing
    to: Paused
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

# Pause in the car or from the notification

## Trigger

The listener pauses from Android's media controls.

## Outcome

Playback pauses where it is.
