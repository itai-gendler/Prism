---
kind: edge
routes:
  main: Main path
steps:
- text: A download fails.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads
- text: The Product keeps the failed download and its progress for another try.
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Downloading
    to: Failed
    facts:
    - Progress
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#download
---

# A download fails

## Trigger

A download fails.

## Outcome

The download shows as failed and can be tried again.
