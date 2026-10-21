---
kind: primary
routes:
  main: Main path
steps:
- text: The listener adds a podcast show to the library.
  kind: actor
  entities:
  - entity: podcast-show
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
- text: The Product adds it to the library in the YouTube Music account and refreshes the library.
  kind: product
  entities:
  - entity: podcast-show
    effect: changes
    facts:
    - Saved
  - entity: account
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
---

# Save a podcast show to the library

## Trigger

The listener wants to follow a show.

## Outcome

The show is in the library once YouTube Music accepts the change.

## Edge cases

- If YouTube Music refuses the change, the library stays as it was and the listener is told.
