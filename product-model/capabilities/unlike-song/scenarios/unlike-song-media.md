---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener uses the like button in the media controls on a liked song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::player
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
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setLiked
---

# Unlike a song in the car

## Trigger

The listener uses the like button on a liked song on the car's player.

## Outcome

The song leaves Liked songs, as it would on the phone.
