---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns shuffle on.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product turns shuffle on with a fresh order that starts from the current song.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Shuffle
    - Order
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

# Turn shuffle on

## Trigger

The listener wants the queue in a random order.

## Outcome

The rest of the queue plays in a fresh random order after the current song; Previous still goes back to what was heard.
