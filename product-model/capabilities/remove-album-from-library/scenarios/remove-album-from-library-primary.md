---
kind: primary
routes:
  main: Main path
steps:
- text: The listener removes an album from the library.
  kind: actor
  entities:
  - entity: album
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
- text: The Product removes it from the library in the YouTube Music account and refreshes the library.
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

# Remove an album from the library

## Trigger

The listener no longer wants an album in their library.

## Outcome

The album leaves the library once YouTube Music accepts the change.

## Edge cases

- If YouTube Music refuses the change, the library stays as it was and the listener is told.
