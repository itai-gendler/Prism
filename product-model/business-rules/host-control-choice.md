---
appliesTo:
- type: entity
  id: together-session
  effect: changes
  facts:
  - Guest control
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#setGuestsControl
permits:
- actors:
  - session-host
---

# Only the session host changes guest playback permission

The host owns the choice that admits playback commands from guests.
