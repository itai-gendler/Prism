---
kind: validation
routes:
  main: Main path
steps:
- text: The session guest enters a code the host does not accept.
  kind: actor
  entities: []
  contexts:
    main:
      place: phone::listen-together
  actor: session-guest
- text: The Product shows the host's reason and leaves the guest outside the session.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - Connection
    from: Joining
    to: Idle
  contexts:
    main:
      place: phone::listen-together
  actor: session-guest
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#join
---

# The host turns the guest away

## Trigger

The code is wrong or the phones run incompatible versions of Prism.

## Outcome

The guest is told why and is not in the session.
