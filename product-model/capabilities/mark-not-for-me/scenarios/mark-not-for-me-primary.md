---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Not for me for a song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product marks the song Not for me, unlikes it, deletes its Smart Downloads copy and, while signed in, tells YouTube
    Music.
  kind: product
  entities:
  - entity: song
    effect: changes
    facts:
    - Not for me
    - Liked
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setDisliked
---

# Mark a song Not for me

## Trigger

The listener does not want to hear a song in recommendations.

## Outcome

The song is left out of autoplay, radio and Smart Downloads, its like is removed and a Smart Downloads copy is deleted.
