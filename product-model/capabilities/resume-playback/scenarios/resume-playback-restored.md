---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener presses play on the queue Prism brought back.
  kind: actor
  entities:
  - entity: queue
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product plays the saved queue from its saved song and position.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Saved position
    - Source
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
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

# Pick up the last queue after reopening Prism

## Trigger

Prism starts again after the listener last listened.

## Outcome

The last queue plays on from the song and position where it stopped.
