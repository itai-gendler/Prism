---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens a podcast show.
  kind: actor
  entities:
  - entity: podcast-show
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
- text: The Product shows the show's description and episodes with each episode's progress.
  kind: product
  entities:
  - entity: podcast-show
    effect: reads
    facts:
    - Title
    - Author
    - Description
    - Episodes
    - Saved
  - entity: episode
    effect: reads
    facts:
    - Title
    - Details
    - Position
    - Last heard
  actor: listener
  contexts:
    main:
      place: phone::podcast
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
---

# Browse a podcast

## Trigger

The listener opens a podcast show.

## Outcome

The show's description and episodes are shown with each episode's progress on this phone.
