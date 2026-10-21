---
kind: primary
routes:
  main: Main path
steps:
- text: The listener confirms cancelling the unfinished downloads.
  kind: actor
  entities:
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product removes the chosen unfinished downloads.
  kind: product
  entities:
  - entity: download
    effect: removes
    from: Queued
  actor: listener
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt#DownloadsInfo
---

# Cancel unfinished downloads

## Trigger

Downloads are waiting or in progress.

## Outcome

The chosen unfinished downloads are cancelled.
