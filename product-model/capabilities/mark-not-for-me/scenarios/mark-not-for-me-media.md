---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener uses Not for me in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::player
- text: The Product marks the song Not for me and skips to the next song when there is one.
  kind: product
  entities:
  - entity: song
    effect: changes
    facts:
    - Not for me
    - Liked
  - entity: queue
    effect: changes
    facts:
    - Current
  - entity: playback
    effect: changes
    facts:
    - Media
    - Position
  actor: listener
  contexts:
    main:
      place: android-media::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setDisliked
---

# Not for me in the car

## Trigger

The listener uses Not for me on the car's player.

## Outcome

The song is marked Not for me and the next song starts.
