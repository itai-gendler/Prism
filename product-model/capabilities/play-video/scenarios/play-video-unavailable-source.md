---
kind: edge
routes:
  main: Main path
steps:
- text: The listener switches to Video for a song whose video cannot be found.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product says whether there is no video or the search failed, and keeps the song playing.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Error
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

# No music video for this song

## Trigger

The song has no music video, or it cannot be found right now.

## Outcome

The listener is told which, the song keeps playing, and the switch can be tried again.
