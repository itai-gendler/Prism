---
appliesTo:
- type: entity
  id: queue
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#maybeAutoplay
---

# Song radio continues independently of ordinary Autoplay

Song-seeded radio remains eligible for continuation with ordinary Autoplay off. Podcast episodes and local-file seeds do not start music autoplay; following a host uses the host’s queue.
