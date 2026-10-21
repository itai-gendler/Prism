---
kind: edge
routes:
  main: Main path
steps:
- text: The listener syncs the library while a request to YouTube Music fails.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::library
- text: The Product records the sync error.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Library sync
  actor: listener
  contexts:
    main:
      place: phone::library
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#sync
---

# The library sync fails

## Trigger

A request to YouTube Music fails during a sync.

## Outcome

The sync shows an error and the library is not shown as empty.
