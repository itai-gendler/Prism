---
kind: primary
routes:
  main: Main path
steps:
- text: The listener likes a song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product records the like and, for a catalog song while signed in, likes it on YouTube Music.
  kind: product
  entities:
  - entity: song
    effect: changes
    facts:
    - Liked
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setLiked
---

# Like a song

## Trigger

The listener likes a song.

## Outcome

The song is in Liked songs; while signed in, a catalog song is liked on YouTube Music too.

## Edge cases

- If YouTube Music does not take the change, Prism says so and keeps the change on the phone.
- Liking or unliking a file on the phone changes nothing on YouTube Music and downloads nothing.
