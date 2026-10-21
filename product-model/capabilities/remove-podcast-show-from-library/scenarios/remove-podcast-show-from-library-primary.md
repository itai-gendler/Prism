---
kind: primary
routes:
  main: Main path
steps:
- text: The listener removes a podcast show from the library.
  kind: actor
  entities:
  - entity: podcast-show
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
- text: The Product removes it from the library in the YouTube Music account and refreshes the library.
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

# Remove a podcast show from the library

## Trigger

The listener no longer follows a show.

## Outcome

The show leaves the library once YouTube Music accepts the change.

## Edge cases

- If YouTube Music refuses the change, the library stays as it was and the listener is told.
