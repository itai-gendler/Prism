---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener asks the assistant to play music on Prism without naming any.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: voice
- text: The Product plays the saved queue from its saved position.
  kind: product
  entities:
  - entity: queue
    effect: reads
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
  actor: listener
  contexts:
    main:
      place: voice
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Carry on by voice

## Trigger

The listener says "play music on Prism" without naming anything.

## Outcome

The last queue plays on from where it stopped; with no saved queue, nothing starts.
