---
kind: primary
routes:
  main: Main path
steps:
- text: The listener dismisses the mini player.
  kind: actor
  entities:
  - entity: playback
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product stops playback and empties the queue.
  kind: product
  entities:
  - entity: playback
    effect: changes
    from: Playing
    to: Stopped
    facts:
    - Position
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Suggestions
    - Added by listener
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Stop playback

## Trigger

The listener is done listening.

## Outcome

Playback stops and the queue is emptied.
