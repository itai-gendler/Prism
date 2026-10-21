---
kind: primary
routes:
  main: Main path
steps:
- text: The listener removes a recent search.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::search
- text: The Product removes it from Recent searches.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Recent searches
  actor: listener
  contexts:
    main:
      place: phone::search
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SearchScreen.kt
---

# Remove a recent search

## Trigger

The listener does not want a recent search suggested.

## Outcome

The search leaves Recent searches.
