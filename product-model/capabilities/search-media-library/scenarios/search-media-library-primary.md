---
kind: primary
routes:
  main: Main path
steps:
- text: The listener searches in the media controls.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::browse
- text: The Product returns matching songs, ranked with the listener's own listening.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Artwork
  actor: listener
  contexts:
    main:
      place: android-media::browse
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/MediaTree.kt#search
---

# Search from the car

## Trigger

The listener searches in Android Auto or another media browser.

## Outcome

Matching songs are listed, best first, or none.
