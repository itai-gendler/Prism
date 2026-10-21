---
kind: edge
routes:
  main: Main path
steps:
- text: Prism is open, online and done loading the music, and some downloads have failed.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  - entity: playback
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads
- text: The Product restarts the failed downloads.
  kind: product
  entities:
  - entity: download
    effect: changes
    from: Failed
    to: Queued
    facts:
    - Waiting
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#retryFailed
---

# Failed downloads retry after reconnecting

## Trigger

Prism is open and back online with failed downloads.

## Outcome

The failed downloads are queued again without the listener asking.
