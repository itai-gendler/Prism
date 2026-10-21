---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener uses the like button in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
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
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setLiked
---

# Like a song in the car

## Trigger

The listener uses the like button on the car's player.

## Outcome

The song is liked, as it would be on the phone.
