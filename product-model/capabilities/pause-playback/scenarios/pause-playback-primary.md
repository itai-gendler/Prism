---
kind: primary
routes:
  main: Main path
steps:
- text: The listener pauses.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
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
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Pause playback

## Trigger

The listener pauses in the player.

## Outcome

Playback pauses where it is, with the queue kept.
