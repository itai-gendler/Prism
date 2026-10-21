---
appliesTo:
- type: entity
  id: together-session
  effect: changes
  facts:
  - Host
  - Code
  - Guests
  - Connection
  - Play here too
  - In step
permits:
- actors:
  - session-host
  - session-guest
- unattended: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt
---

# The host and guests start, join and leave sessions

The host starts and ends the session; a guest joins, plays along, catches up or leaves. Prism itself ends a guest's session when the host is lost and marks a guest out of step.
