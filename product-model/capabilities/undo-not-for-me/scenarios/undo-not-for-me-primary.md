---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns Not for me off for the song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product takes the mark off and, while signed in, tells YouTube Music.
  kind: product
  entities:
  - entity: song
    effect: changes
    facts:
    - Not for me
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setDisliked
---

# Undo Not for me

## Trigger

A song is marked Not for me.

## Outcome

The song can come up in recommendations again.
