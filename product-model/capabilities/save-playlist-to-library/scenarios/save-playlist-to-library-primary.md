---
kind: primary
routes:
  main: Main path
steps:
- text: The listener adds a playlist to the library.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product adds it to the library in the YouTube Music account and refreshes the library.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Saved
  - entity: account
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# Save a playlist to the library

## Trigger

The listener wants someone else's playlist in their library.

## Outcome

The playlist is in the library once YouTube Music accepts the change.

## Edge cases

- If YouTube Music refuses the change, the library stays as it was and the listener is told.
