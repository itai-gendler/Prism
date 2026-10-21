---
kind: edge
routes:
  main: Main path
steps:
- text: The listener opens an album that has no saved copy, and the request to YouTube Music fails.
  kind: actor
  entities:
  - entity: album
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
- text: The Product shows that the album could not be loaded and offers to try again.
  kind: product
  entities:
  - entity: album
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# An album that cannot be loaded

## Trigger

An album with no saved copy cannot be loaded from YouTube Music.

## Outcome

The listener sees that the album could not be loaded and can try again.
