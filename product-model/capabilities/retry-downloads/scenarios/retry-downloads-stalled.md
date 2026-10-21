---
kind: edge
routes:
  main: Main path
steps:
- text: A download makes no progress for several checks while online.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads
- text: The Product restarts it from where it got to.
  kind: product
  entities:
  - entity: download
    effect: changes
    facts:
    - Progress
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#retryFailed
---

# A stuck download restarts

## Trigger

A download has made no progress for a while although the phone is online.

## Outcome

The download picks up again from where it got to.
