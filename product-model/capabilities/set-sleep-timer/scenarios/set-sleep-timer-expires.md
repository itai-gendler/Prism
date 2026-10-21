---
kind: edge
routes:
  main: Main path
steps:
- text: The sleep timer's time is up, or the song it waits for ends.
  kind: condition
  entities:
  - entity: song
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::player
- text: The Product pauses playback and clears the timer.
  kind: product
  entities:
  - entity: playback
    effect: changes
    from: Playing
    to: Paused
    facts:
    - Sleep timer
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# The sleep timer runs out

## Trigger

The chosen time passes or the current song ends.

## Outcome

Playback pauses and the timer is cleared.
