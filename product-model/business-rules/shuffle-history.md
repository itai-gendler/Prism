---
appliesTo:
- type: entity
  id: queue
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/HistoryShuffleOrder.kt
---

# Shuffle preserves the path already heard

A new shuffle starts at the current entry. Play next becomes next in play order; a jump to a queued entry records it after the previously current entry so Previous can return there.
