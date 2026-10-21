---
appliesTo:
- type: entity
  id: download
  effect: creates
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/SmartDownloads.kt
permits:
- actors:
  - listener
- unattended: true
  when:
  - entity: preferences
    fact: Smart Downloads
    is: true
---

# The listener starts downloads, and Smart Downloads adds its picks only while it is on

The listener downloads songs and videos; Smart Downloads downloads its picks on its own schedule, and only while it is turned on.
