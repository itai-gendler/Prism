---
kind: alternate
routes:
  main: Main path
steps:
- text: The session guest uses play in the session.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product sends play to the host and shows the host's new state.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - Now playing
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Resume the host's music as a guest

## Trigger

The host lets guests control playback.

## Outcome

The host's music plays on for everyone following it.
