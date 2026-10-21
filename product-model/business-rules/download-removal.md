---
appliesTo:
- type: entity
  id: download
  effect: removes
permits:
- actors:
  - listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt
---

# The listener removes downloads

Cancelling and removing affect only the downloads the listener chose, or Smart Downloads' picks when clearing them.
