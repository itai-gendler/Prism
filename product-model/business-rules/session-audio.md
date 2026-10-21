---
appliesTo:
- type: entity
  id: together-session
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt
---

# Listen together shares playback state rather than audio

Phones exchange current music, queue and control state over the local network; each phone obtains its own audio. Prism has no internet relay for these sessions and does not promise exact cross-device synchronization.
