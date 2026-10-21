---
kind: edge
routes:
  main: Main path
steps:
- text: A queued download starts on an allowed network.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads
- text: The Product shows the download's progress as it arrives.
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Queued
    to: Downloading
    facts:
    - Progress
    - Waiting
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#download
---

# A download starts

## Trigger

A queued download is on an allowed network.

## Outcome

Downloads shows the song's progress as it arrives.
