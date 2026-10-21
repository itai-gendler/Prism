---
kind: edge
routes:
  main: Main path
steps:
- text: A song's stream fails during playback.
  kind: condition
  entities:
  - entity: playback
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::player
- text: The Product refreshes the stream and tries up to twice more, then reports the error and moves to the next song when
    there is one.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Error
    - Media
    - Position
  - entity: queue
    effect: changes
    facts:
    - Current
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/AppContainer.kt
---

# A song's stream fails

## Trigger

A song's stream stops working during playback.

## Outcome

Prism tries the stream again; if it still fails, it shows an error and moves to the next song when there is one.
