---
kind: edge
routes:
  main: Main path
steps:
- text: The session guest tries to join a session whose host does not answer.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: A connection attempt is under way.
  kind: condition
  entities:
  - entity: together-session
    effect: reads
    facts:
    - Connection
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product gives up and says the host could not be reached.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Joining
    to: Idle
    facts:
    - Connection
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#join
---

# The host cannot be reached

## Trigger

The host does not answer.

## Outcome

The guest is told the host could not be reached and is not in the session.
