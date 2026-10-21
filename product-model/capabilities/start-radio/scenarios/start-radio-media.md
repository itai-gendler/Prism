---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener uses Start radio in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product keeps the current song and position and replaces what is up next with the radio's songs.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Source
    - Suggestions
  - entity: playback
    effect: reads
    facts:
    - Media
    - Position
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# Start radio in the car

## Trigger

The listener uses Start radio on the car's player.

## Outcome

The current song keeps playing and the radio's songs follow it.
