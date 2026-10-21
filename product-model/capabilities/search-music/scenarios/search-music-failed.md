---
kind: edge
routes:
  main: Main path
steps:
- text: The listener searches the catalog.
  kind: actor
  entities: []
  contexts:
    main:
      place: phone::search
  actor: listener
- text: The Product shows that the search failed and offers to try again.
  kind: product
  entities: []
  contexts:
    main:
      place: phone::search
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SearchScreen.kt
---

# Search fails

## Trigger

The search request to YouTube Music fails.

## Outcome

The listener sees the error and can search again.
