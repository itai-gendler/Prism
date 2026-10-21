---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener chooses Play next for a song or collection while nothing is queued.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product starts the song or collection as a new queue.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Source
    - Order
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
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerQueue.kt
---

# Play next with nothing playing

## Trigger

Nothing is queued when the listener chooses Play next.

## Outcome

The chosen song or collection starts playing as a new queue.
