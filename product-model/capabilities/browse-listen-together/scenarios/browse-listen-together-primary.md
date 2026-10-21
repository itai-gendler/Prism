---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Listen together.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::listen-together
- text: The Product lists the sessions it finds on the network.
  kind: product
  entities:
  - entity: together-session
    effect: reads
    facts:
    - Host
    - Code
    - Guests
    - Guest control
    - Now playing
    - Play here too
    - In step
    - Connection
  actor: listener
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/TogetherScreen.kt
---

# Find sessions nearby

## Trigger

The listener opens Listen together while not in a session.

## Outcome

Sessions on the same network are listed to join, beside the option to start one.
