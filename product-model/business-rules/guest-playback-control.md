---
appliesTo:
- type: entity
  id: together-session
  effect: changes
  facts:
  - Now playing
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#serveGuest
permits:
- actors:
  - session-guest
  when:
  - fact: Guest control
    is: true
---

# Guests control host playback only when the host allows it

Joined guests can send play, pause, next, previous and seek commands; the host applies them only while guest control is enabled.
