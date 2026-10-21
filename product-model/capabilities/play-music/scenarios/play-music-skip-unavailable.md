---
kind: edge
routes:
  main: Main path
steps:
- text: A song ends while the phone is offline.
  kind: condition
  entities:
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
  unattended: true
- text: The Product skips upcoming songs that cannot play offline when a later one can.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Current
  - entity: playback
    effect: changes
    facts:
    - Media
    - Position
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#onMediaItemTransition
---

# Skip songs that cannot play offline

## Trigger

A song ends while the phone is offline.

## Outcome

Playback moves on to the next song that can play offline.
