---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Try again.
  kind: actor
  entities:
  - entity: download
    effect: reads
    facts: []
  actor: listener
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
  actor: listener
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#retryFailed
---

# Try failed downloads again

## Trigger

Some downloads have failed.

## Outcome

The failed downloads are queued again.
