---
kind: primary
routes:
  main: Main path
steps:
- text: The session host chooses End session.
  kind: actor
  entities: []
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
- text: The Product ends the session, stops advertising it and tells the connected guests.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Hosting
    to: Idle
    facts:
    - Guests
    - Connection
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#leave
---

# End the session

## Trigger

The host is done listening together.

## Outcome

The session ends, stops showing on the network and its guests are told.
