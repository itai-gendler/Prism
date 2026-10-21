---
kind: edge
routes:
  main: Main path
steps:
- text: The listener opens the lyrics.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
  actor: listener
- text: The Product finds no usable lyrics and says so.
  kind: product
  entities:
  - entity: lyrics
    effect: reads
    facts:
    - Text
    - Source
  contexts:
    main:
      place: phone::player
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt#loadAuto
---

# No lyrics for this song

## Trigger

No source has usable lyrics for the song.

## Outcome

The listener sees that there are no lyrics for this song.
