---
kind: edge
routes:
  main: Main path
steps:
- text: The listener opens an artist.
  kind: actor
  entities:
  - entity: artist
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::artist
  actor: listener
- text: The Product shows that the artist could not be loaded and offers to try again.
  kind: product
  entities:
  - entity: artist
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::artist
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ArtistScreen.kt
---

# An artist page that cannot be loaded

## Trigger

The artist page cannot be fetched from YouTube Music.

## Outcome

The listener sees that the page could not be loaded and can try again.
