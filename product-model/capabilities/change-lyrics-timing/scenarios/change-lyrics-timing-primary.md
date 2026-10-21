---
kind: primary
routes:
  main: Main path
steps:
- text: The listener moves the song's lyrics earlier or later in Lyrics timing.
  kind: actor
  entities:
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
- text: The Product keeps the timing for this song and uses it for highlighting lyric lines and for seeking from them.
  kind: product
  entities:
  - entity: lyrics
    effect: changes
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
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt#setLyricOffset
---

# Change lyrics timing

## Trigger

The lyrics run ahead of or behind the singing for this song.

## Outcome

The song's lyrics light up earlier or later from now on; Reset puts them back in step.
