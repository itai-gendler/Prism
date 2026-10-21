---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Play next.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product puts the music straight after the current song.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Order
    - Added by listener
    - Suggestions
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

# Play next

## Trigger

The listener wants music straight after the current song.

## Outcome

The music plays right after the current song.
