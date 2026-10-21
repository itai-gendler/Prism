---
kind: primary
routes:
  main: Main path
steps:
- text: The listener presses previous.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
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
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Skip to previous

## Trigger

The listener presses previous.

## Outcome

The song restarts, or the song heard before it plays, shuffled or not.
