---
kind: primary
routes:
  main: Main path
steps:
- text: The listener uses repeat.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
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
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Change repeat

## Trigger

The listener uses repeat in the player.

## Outcome

Repeat moves from off to all to one and back to off.
