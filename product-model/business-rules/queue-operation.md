---
appliesTo:
- type: entity
  id: queue
  effect: changes
  facts:
  - Entries
  - Current
  - Order
  - Source
  - Suggestions
  - Added by listener
  - Shuffle
  - Repeat
  - Saved position
permits:
- actors:
  - listener
  - session-guest
- unattended: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# The listener and session guests change the queue

The listener changes their own queue; a guest's songs and controls reach the host's queue; Prism itself adds autoplay suggestions and keeps the queue's position. Rearranging by hand has its own condition.
