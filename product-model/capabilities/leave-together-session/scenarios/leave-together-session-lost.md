---
kind: edge
routes:
  main: Main path
steps:
- text: The connection to the host drops and the reconnection attempts fail.
  kind: condition
  entities: []
  unattended: true
  contexts:
    main:
      place: phone::listen-together
- text: The Product ends the guest's session and says the connection was lost.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Joined
    to: Idle
    facts:
    - Connection
    - In step
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#leave
---

# The connection to the host is lost

## Trigger

The connection to the host drops and a few reconnection attempts fail.

## Outcome

The guest is out of the session and told the connection was lost.
