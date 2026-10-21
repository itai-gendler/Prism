---
appliesTo:
- type: entity
  id: queue
  effect: changes
  facts:
  - Manual arrangement
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerQueue.kt
permits:
- actors:
  - listener
  when:
  - fact: Shuffle
    is: false
---

# Only an unshuffled queue can be manually reordered

The phone queue disables reorder while shuffle is active. Play next and Add to queue remain separate operations.
