---
kind: edge
routes:
  main: Main path
steps:
- text: A song finishes downloading.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads
- text: The Product marks the download completed and saves the song's lyrics, cover and animated cover when they can be found.
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Completed
    facts:
    - Progress
    - Lyrics level
  - entity: lyrics
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#download
---

# A download finishes

## Trigger

A song finishes downloading.

## Outcome

The song is in Downloads and plays offline, with its lyrics and cover saved when they can be found.
