---
kind: edge
routes:
  main: Main path
steps:
- text: Playback nears the end of a queue with Autoplay on.
  kind: condition
  entities:
  - entity: playback
    effect: reads
    facts: []
  - entity: queue
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::player
- text: The Product adds similar songs from YouTube Music, leaving out songs already queued and songs marked Not for me.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Suggestions
  - entity: song
    effect: reads
    facts:
    - Not for me
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#onAutoplayChanged
---

# Autoplay tops up the queue

## Trigger

Autoplay is on and playback nears the end of the queue.

## Outcome

Similar songs join the end of the queue, leaving out songs already queued and songs marked Not for me.
