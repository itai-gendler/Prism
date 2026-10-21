---
kind: primary
routes:
  main: Main path
steps:
- text: The session guest picks a session and enters its code.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product starts joining the session.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Idle
    to: Joining
    facts:
    - Host
    - Code
    - Connection
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The host has accepted the code and the guest's version of Prism.
  kind: condition
  entities:
  - entity: together-session
    effect: reads
    facts:
    - Connection
  contexts:
    main:
      place: phone::listen-together
- text: The Product joins the session and shows it.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Joining
    to: Joined
    facts:
    - Host
    - Guests
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
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#join
---

# Join a session

## Trigger

A friend is hosting a session on the same network.

## Outcome

The guest is in the session and sees what is playing.
