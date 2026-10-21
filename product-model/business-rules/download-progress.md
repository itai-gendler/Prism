---
appliesTo:
- type: entity
  id: download
  effect: changes
permits:
- actors:
  - listener
- unattended: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt
---

# The listener retries downloads, and Prism keeps their progress

The listener can try failed downloads again and fetch missing lyrics; Prism itself moves downloads through their progress, and retries failed or stuck ones.
