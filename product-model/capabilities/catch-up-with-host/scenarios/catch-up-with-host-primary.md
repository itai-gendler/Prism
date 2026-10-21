---
kind: primary
routes:
  main: Main path
steps:
- text: The session guest taps Out of step.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product plays the host's current music and position on this phone again.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - In step
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
  - entity: playback
    effect: changes
    facts:
    - Media
    - Position
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#resync
---

# Catch up with the host

## Trigger

The guest's phone is out of step with the host.

## Outcome

The guest's phone plays what the host plays, from the host's position, again.
