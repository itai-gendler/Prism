---
kind: primary
routes:
  main: Main path
steps:
- text: The listener removes a playlist from the library.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product removes it from the library in the YouTube Music account and refreshes the library.
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

# Remove a playlist from the library

## Trigger

The listener no longer wants a saved playlist in their library.

## Outcome

The playlist leaves the library once YouTube Music accepts the change.

## Edge cases

- If YouTube Music refuses the change, the library stays as it was and the listener is told.
