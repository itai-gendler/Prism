---
kind: primary
routes:
  main: Main path
steps:
- text: The listener browses Prism in Android Auto or another media browser.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: android-media::browse
- text: The Product supplies its music lists, each list of more than one song starting with Shuffle play.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Duration
    - Artwork
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Picture
  - entity: album
    effect: reads
    facts:
    - Title
    - Artists
    - Artwork
  - entity: download
    effect: reads
    facts:
    - Track
  - entity: listening-history
    effect: reads
    facts:
    - Recent music
  actor: listener
  contexts:
    main:
      place: android-media::browse
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/MediaTree.kt
---

# Browse Prism in the car

## Trigger

The listener browses Prism from Android Auto or another media browser.

## Outcome

Home, Liked songs, the library, Downloads and recent plays are listed, each song list starting with Shuffle play.

## Edge cases

- When YouTube Music cannot be reached, lists that need it come back empty; Home keeps the shelves it has.
