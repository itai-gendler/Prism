---
kind: primary
routes:
  main: Main path
steps:
- text: The session guest chooses Leave.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product disconnects from the host and stops following it.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Joined
    to: Idle
    facts:
    - Connection
    - Play here too
    - In step
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#leave
---

# Leave a session

## Trigger

The guest is done listening together.

## Outcome

The guest is out of the session and their phone stops following the host.
