---
kind: primary
routes:
  main: Main path
steps:
- text: The listener unlikes a song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product removes the like and, for a catalog song while signed in, unlikes it on YouTube Music.
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

# Unlike a song

## Trigger

The listener unlikes a song.

## Outcome

The song leaves Liked songs; while signed in, a catalog song is unliked on YouTube Music too.

## Edge cases

- If YouTube Music does not take the change, Prism says so and keeps the change on the phone.
- Liking or unliking a file on the phone changes nothing on YouTube Music and downloads nothing.
