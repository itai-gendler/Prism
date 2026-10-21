---
kind: primary
routes:
  main: Main path
steps:
- text: The listener presses play.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
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
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Resume playback

## Trigger

Playback is paused.

## Outcome

Playback carries on from where it paused.
