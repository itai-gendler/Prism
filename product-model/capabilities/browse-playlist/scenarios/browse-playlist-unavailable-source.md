---
kind: edge
routes:
  main: Main path
steps:
- text: The listener opens a playlist that has no saved copy, and the request to YouTube Music fails.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product shows that the playlist could not be loaded and offers to try again.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# A playlist that cannot be loaded

## Trigger

A playlist with no saved copy cannot be loaded from YouTube Music.

## Outcome

The listener sees that the playlist could not be loaded and can try again.
