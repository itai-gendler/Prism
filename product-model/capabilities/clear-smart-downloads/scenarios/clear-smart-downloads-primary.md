---
kind: primary
routes:
  main: Main path
steps:
- text: The listener clears Smart Downloads.
  kind: actor
  entities:
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads-storage
- text: The Product removes Smart Downloads' picks and empties the streamed-music cache.
  kind: product
  entities:
  - entity: download
    effect: removes
    from: Completed
  actor: listener
  contexts:
    main:
      place: phone::downloads-storage
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#clearSmartDownloads
---

# Clear Smart Downloads

## Trigger

The listener wants the space Smart Downloads uses back.

## Outcome

Smart Downloads' picks and the streamed-music cache are emptied; songs the listener downloaded stay.
