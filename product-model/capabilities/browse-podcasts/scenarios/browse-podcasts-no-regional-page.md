---
kind: edge
routes:
  main: Main path
steps:
- text: The listener opens Podcasts and YouTube Music returns no shows.
  kind: actor
  entities: []
  contexts:
    main:
      place: phone::podcasts
  actor: listener
- text: The Product explains that Podcasts is not available in this region and points to search.
  kind: product
  entities: []
  contexts:
    main:
      place: phone::podcasts
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
---

# Podcasts not offered in the listener's region

## Trigger

YouTube Music returns no podcast shows or shelves for the listener's region.

## Outcome

The listener is told Podcasts is not available here and pointed to search for shows and episodes.
