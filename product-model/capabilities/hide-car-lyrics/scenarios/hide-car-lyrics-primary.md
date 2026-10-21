---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns car lyrics off with the lyrics button on the car's player.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product turns car lyrics off and sends the song's own title and cover again.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Car lyrics
  - entity: song
    effect: reads
    facts: []
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#onCustomCommand
---

# Turn car lyrics off

## Trigger

Car lyrics are showing on the car's player.

## Outcome

The car's player shows the song title and cover again.
