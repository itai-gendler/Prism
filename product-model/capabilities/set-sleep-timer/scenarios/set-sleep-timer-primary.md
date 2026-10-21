---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks a duration or end of song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product sets the timer, replacing any other.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Sleep timer
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Set a sleep timer

## Trigger

The listener wants the music to stop by itself.

## Outcome

Playback will pause after the chosen time or at the end of the current song.
