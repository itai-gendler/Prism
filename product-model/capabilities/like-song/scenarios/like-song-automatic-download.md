---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener likes a catalog song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
  actor: listener
- text: The Product records the like and starts downloading the song.
  kind: product
  entities:
  - entity: song
    effect: changes
    facts:
    - Liked
  - entity: download
    effect: creates
    facts:
    - Track
    - Origin
    - Added
    to: Queued
  contexts:
    main:
      place: phone::player
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setLiked
---

# Liking a song downloads it

## Trigger

Automatic downloads of liked songs are on.

## Outcome

The song is liked and queued to download.
