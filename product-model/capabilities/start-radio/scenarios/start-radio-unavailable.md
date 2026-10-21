---
kind: edge
routes:
  main: Main path
steps:
- text: The listener chooses Radio and YouTube Music returns no usable songs.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product starts no radio; on the phone it reports the failure, and in the car it keeps the current queue.
  kind: product
  entities:
  - entity: queue
    effect: reads
    facts:
    - Entries
    - Current
    - Order
    - Source
    - Suggestions
    - Added by listener
    - Shuffle
    - Repeat
    - Saved position
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
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# No radio available

## Trigger

YouTube Music returns no radio for the choice.

## Outcome

No radio starts; on the phone the listener is told, and in the car the current queue stays.
