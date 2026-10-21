---
appliesTo:
- type: entity
  id: listening-history
- type: capability
  id: play-music
- type: capability
  id: pause-playback
- type: capability
  id: stop-playback
- type: capability
  id: skip-next
- type: capability
  id: skip-previous
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#flushPlayTime
---

# Replay counts music played on this phone

A song counts once it has played for at least ten seconds, with the time it was heard. Podcast episodes do not count toward Replay. Recently played is kept separately, from when each song starts.
