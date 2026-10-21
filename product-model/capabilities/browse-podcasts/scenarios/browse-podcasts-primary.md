---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Podcasts.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::podcasts
- text: The Product shows popular shows, followed shows and episodes to continue.
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
      place: phone::podcasts
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
---

# Browse Podcasts

## Trigger

The listener opens Podcasts.

## Outcome

Popular shows, followed shows when signed in and episodes to continue are shown.
