---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens an album.
  kind: actor
  entities:
  - entity: album
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::album
- text: The Product shows the album's release details, cover and tracks.
  kind: product
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artists
    - Release
    - Tracks
    - Artwork
    - Saved
    - Offline copy
  actor: listener
  contexts:
    main:
      place: phone::album
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Browse an album

## Trigger

The listener opens an album.

## Outcome

The album's release details and tracks are shown, with its most-played songs marked when YouTube Music supplies them.
