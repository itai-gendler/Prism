---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener asks the assistant to play named music on Prism.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: voice
- text: The Product searches for songs and plays the best match.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
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
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/AppContainer.kt
---

# Play by voice

## Trigger

The listener asks the assistant to play something on Prism.

## Outcome

The best-matching song starts playing.
