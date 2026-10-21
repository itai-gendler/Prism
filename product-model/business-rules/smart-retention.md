---
appliesTo:
- type: entity
  id: download
- type: entity
  id: preferences
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/SmartDownloads.kt
---

# Smart Downloads and streamed audio share the chosen space

Predictive picks use at most three quarters of the chosen budget and leave a free-space reserve. Runs add a slice gradually and rotate out at most 25 completed obsolete picks; manually downloaded audio is not the predictive eviction set.
