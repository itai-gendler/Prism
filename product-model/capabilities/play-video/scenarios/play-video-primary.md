---
kind: primary
routes:
  main: Main path
steps:
- text: The listener switches to Video.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product finds the song's music video and switches to it at the matching position.
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

# Switch to the music video

## Trigger

The listener wants to watch the song's music video.

## Outcome

The video plays from the same spot, with the lyrics still in step.
