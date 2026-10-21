---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener switches search to the phone and types.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::search
- text: The Product lists matching local files and downloads.
  kind: product
  entities:
  - entity: music-file
    effect: reads
    facts:
    - Location
    - Tags
    - Format
    - Added
    - Embedded lyrics
    - Access
  - entity: download
    effect: reads
    facts:
    - Track
    - Progress
    - Origin
    - Added
    - Lyrics level
    - Waiting
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Duration
    - Artwork
    - Source
    - Liked
    - Not for me
    - Last played
  actor: listener
  contexts:
    main:
      place: phone::search
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SearchScreen.kt
---

# Search music on the phone

## Trigger

The listener wants music already on the phone, or is offline.

## Outcome

Matching local files and downloads are listed without asking YouTube Music.
