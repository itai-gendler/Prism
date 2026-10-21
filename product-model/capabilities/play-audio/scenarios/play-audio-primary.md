---
kind: primary
routes:
  main: Main path
steps:
- text: The listener switches to Song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product switches from the video to the song at the matching position, keeping it playing or paused.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Mode
    - Position
  - entity: lyrics
    effect: reads
    facts:
    - Offset
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
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#setVideoMode
---

# Switch back to the song

## Trigger

A music video is playing.

## Outcome

The song plays on from the same spot, playing or paused as before.
