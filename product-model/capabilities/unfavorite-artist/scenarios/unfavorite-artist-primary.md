---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns Favourite off for an artist.
  kind: actor
  entities:
  - entity: artist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::artist
- text: The Product removes the favourite and unsubscribes on YouTube Music when signed in.
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

# Remove an artist from the favourites

## Trigger

The listener no longer wants an artist among their favourites.

## Outcome

The artist is no longer a favourite and, while signed in, no longer subscribed on YouTube Music.

## Edge cases

- If the YouTube Music subscription cannot be changed, Prism says so and keeps the favourite choice on the phone.
