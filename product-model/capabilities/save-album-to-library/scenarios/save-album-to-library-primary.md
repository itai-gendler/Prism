---
kind: primary
routes:
  main: Main path
steps:
- text: The listener adds an album to the library.
  kind: actor
  entities:
  - entity: album
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
- text: The Product adds it to the library in the YouTube Music account and refreshes the library.
  kind: product
  entities:
  - entity: album
    effect: changes
    facts:
    - Saved
  - entity: account
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# Save an album to the library

## Trigger

The listener wants an album in their library.

## Outcome

The album is in the library once YouTube Music accepts the change.

## Edge cases

- If YouTube Music refuses the change, the library stays as it was and the listener is told.
