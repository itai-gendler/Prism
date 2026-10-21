---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener presses play in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product prepares the music if needed and plays on.
  kind: product
  entities:
  - entity: playback
    effect: changes
    from: Paused
    to: Playing
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

# Resume in the car or from the notification

## Trigger

The listener presses play in Android's media controls.

## Outcome

Playback carries on from where it paused.
