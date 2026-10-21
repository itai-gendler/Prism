---
kind: primary
routes:
  main: Main path
steps:
- text: The listener asks for a song or collection offline.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product starts downloading each song's audio and fetches its lyrics and loudness.
  kind: product
  entities:
  - entity: download
    effect: creates
    to: Queued
    facts:
    - Track
    - Origin
    - Added
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
  target: app/src/main/java/com/prism/music/download/Downloads.kt#download
---

# Download music

## Trigger

The listener wants a song, album or playlist offline.

## Outcome

The songs are queued to download, with their lyrics and loudness fetched so they work offline.

## Edge cases

- A song already downloaded or downloading is not downloaded twice.
- A lossless file from the phone that was removed from Downloads comes back to the list instead of being downloaded.
- A file already on the phone is not downloaded.
