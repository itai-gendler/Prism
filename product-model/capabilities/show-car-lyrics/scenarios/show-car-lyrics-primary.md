---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns car lyrics on with the lyrics button on the car's player.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product sends the lyrics to the car's player in the chosen style.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Car lyrics
  - entity: lyrics
    effect: reads
    facts:
    - Text
    - Timing
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#onCustomCommand
---

# Turn car lyrics on

## Trigger

The listener wants lyrics on the car's player, for passengers or while parked.

## Outcome

The car's player shows the sung line in place of the title, in the chosen style.
