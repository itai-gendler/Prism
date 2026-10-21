---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns Autoplay off.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product turns Autoplay off and takes its upcoming suggestions out of the queue.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Autoplay
  - entity: queue
    effect: changes
    facts:
    - Entries
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
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#onAutoplayChanged
---

# Turn Autoplay off

## Trigger

The listener does not want similar music added after the queue.

## Outcome

Autoplay's upcoming suggestions leave the queue; a song radio keeps going as radio.
