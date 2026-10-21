---
kind: edge
routes:
  main: Main path
steps:
- text: The listener enters a name and visibility and confirms.
  kind: actor
  entities: []
  contexts:
    main:
      place: phone::library
  actor: listener
- text: The Product reports that it could not be made.
  kind: product
  entities: []
  contexts:
    main:
      place: phone::library
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
---

# The playlist cannot be made

## Trigger

YouTube Music does not make the new playlist.

## Outcome

The listener is told the playlist could not be made, and nothing is added to the library.
