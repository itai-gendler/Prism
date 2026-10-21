---
kind: primary
routes:
  main: Main path
steps:
- text: The listener moves playlists into the order they want.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::library
- text: The Product keeps the order; playlists not yet placed come first, in the order YouTube Music lists them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Library
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::library
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#inOrder
---

# Put library playlists in order

## Trigger

The listener wants their playlists in their own order.

## Outcome

Library lists the playlists in the chosen order; playlists added later come first.
