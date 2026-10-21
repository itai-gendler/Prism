---
appliesTo:
- type: entity
  id: playback
- type: entity
  id: preferences
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#mayBlend
---

# Crossfade applies only to eligible music transitions

Enabled crossfade excludes live streams, video playback, episodes and active Listen together. Consecutive tracks from the same album play straight through when the queue was started as that album; a playlist or radio containing that pair can still blend.
