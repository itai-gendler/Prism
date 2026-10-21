---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Downloads.
  kind: actor
  entities:
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product lists downloaded songs and saved music videos with progress, size and saved lyrics.
  kind: product
  entities:
  - entity: download
    effect: reads
    facts:
    - Track
    - Progress
    - Origin
    - Added
    - Lyrics level
    - Waiting
  - entity: saved-video
    effect: reads
    facts:
    - Track
    - Progress
    - Status
  - entity: lyrics
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Browse Downloads

## Trigger

The listener opens Downloads.

## Outcome

Downloaded songs and saved music videos are listed with their size, saved lyrics and any downloads still in progress.
