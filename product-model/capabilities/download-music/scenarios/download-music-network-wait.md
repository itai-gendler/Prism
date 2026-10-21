---
kind: edge
routes:
  main: Main path
steps:
- text: A download is queued while its network requirement is not met.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads
- text: The Product keeps it queued and shows that it is waiting for Wi-Fi.
  kind: product
  entities:
  - entity: download
    effect: changes
    facts:
    - Waiting
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#download
---

# A download waits for Wi-Fi

## Trigger

Downloads are set to Wi-Fi only and the phone is on mobile data.

## Outcome

The download waits and Downloads says it is waiting for Wi-Fi.
