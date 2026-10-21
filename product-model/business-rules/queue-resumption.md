---
appliesTo:
- type: entity
  id: queue
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#saveQueue
---

# Queue resumption retains media and position

Prism saves queue entries, selected index, position and title locally and restores a nonempty saved queue ready for the listener to resume.
