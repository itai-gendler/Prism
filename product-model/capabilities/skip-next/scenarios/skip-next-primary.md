---
kind: primary
routes:
  main: Main path
steps:
- text: The listener presses next.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
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
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Skip to next

## Trigger

The listener presses next.

## Outcome

The next song in play order starts.
