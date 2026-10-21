---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks a photo or a track cover for the collection, or resets it.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product keeps the picture on this phone and shows it for the collection.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Picture
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/PlaylistCovers.kt
---

# Change a playlist picture

## Trigger

The listener wants their own picture on a playlist, Liked songs or Downloads.

## Outcome

The collection shows the chosen picture on this phone; Reset brings back its own artwork.

## Edge cases

- A picture that cannot be read leaves the current one in place.
