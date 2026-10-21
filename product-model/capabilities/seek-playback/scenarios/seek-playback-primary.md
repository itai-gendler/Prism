---
kind: primary
routes:
  main: Main path
steps:
- text: The listener seeks.
  kind: actor
  entities:
  - entity: playback
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product moves playback to the position, allowing for the song's lyrics timing when seeking from a lyric line.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Position
  - entity: lyrics
    effect: reads
    facts: []
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
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Seek playback

## Trigger

The listener drags the progress bar, holds previous or next, or taps a timed lyric line.

## Outcome

Playback moves to the chosen position, the configured step, or the lyric line's time.
