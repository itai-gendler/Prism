---
kind: edge
routes:
  main: Main path
steps:
- text: The music video fails or shows no picture in time.
  kind: condition
  entities: []
  unattended: true
  contexts:
    main:
      place: phone::player
- text: The Product goes back to the song rather than moving to the next one.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Mode
    - Error
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#setVideoMode
---

# The video does not play

## Trigger

The music video fails or shows no picture.

## Outcome

Playback goes back to the song instead of skipping to another song.
