---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Favourite on an artist.
  kind: actor
  entities:
  - entity: artist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::artist
- text: The Product keeps the artist as a favourite and subscribes to it on YouTube Music when signed in.
  kind: product
  entities:
  - entity: artist
    effect: changes
    facts:
    - Favourite
  actor: listener
  contexts:
    main:
      place: phone::artist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#setFavoriteArtist
---

# Favourite an artist

## Trigger

The listener wants an artist at the top of their library.

## Outcome

The artist is a favourite on this phone and, while signed in, subscribed on YouTube Music.

## Edge cases

- If the YouTube Music subscription cannot be changed, Prism says so and keeps the favourite choice on the phone.
