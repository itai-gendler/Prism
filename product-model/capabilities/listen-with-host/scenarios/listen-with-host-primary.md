---
kind: primary
routes:
  main: Main path
steps:
- text: The session guest turns on Play here too.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product replaces this phone's queue with the host's and follows the host's position.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - Play here too
    - In step
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Order
    - Shuffle
    - Repeat
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
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
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#setListenHere
---

# Play the host's music on this phone

## Trigger

A guest wants to hear the session on their own phone.

## Outcome

The guest's phone plays the host's music, kept in step with the host.
