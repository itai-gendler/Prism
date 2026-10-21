---
kind: primary
routes:
  main: Main path
steps:
- text: The listener shares a Replay story card.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::replay
- text: The Product makes an image of the card and hands it to Android sharing.
  kind: product
  entities:
  - entity: listening-history
    effect: reads
    facts:
    - Music
    - Time heard
  actor: listener
  contexts:
    main:
      place: phone::replay
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ReplayStory.kt
---

# Share Replay

## Trigger

The listener wants to show off their Replay.

## Outcome

A Replay story card is handed to Android sharing.
