---
appliesTo:
- type: entity
  id: together-session
  effect: changes
  to: Joined
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#serveGuest
permits:
- actors:
  - session-guest
  when:
  - fact: Connection
    is: Welcomed
---

# A guest joins only after the host accepts the code and version

Prism’s host checks the joining code and protocol compatibility before welcoming a guest. Failure returns a reason and leaves the guest outside the session.
