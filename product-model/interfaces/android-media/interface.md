---
type: device
actors:
- listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/MediaTree.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# Android media controls

Prism supplies browsing and playback operations to Android Auto and compatible Android media controls. The controller decides which supplied controls and metadata it displays.
