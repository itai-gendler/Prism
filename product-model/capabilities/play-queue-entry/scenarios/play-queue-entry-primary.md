---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks a song in the queue.
  kind: actor
  entities:
  - entity: queue
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product plays it; when shuffled, it becomes next in the shuffled order so Previous comes back to the song before
    it.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Current
    - Order
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
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt#skipTo
---

# Jump to a song in the queue

## Trigger

The listener picks a song in the queue.

## Outcome

That song plays now; when shuffled, Previous still returns to the song that was playing.
