---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener plays a song from Local files.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
  actor: listener
- text: The Product plays the file from the phone.
  kind: product
  entities:
  - entity: music-file
    effect: reads
    facts:
    - Location
    - Format
  - entity: playback
    effect: changes
    facts:
    - Media
    - Position
    - Source details
    from: Stopped
    to: Playing
  contexts:
    main:
      place: phone::player
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#losslessFileFor
---

# Play a file on the phone

## Trigger

The listener plays a song from Local files.

## Outcome

The file plays in place, from the phone.
