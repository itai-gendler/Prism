---
kind: alternate
routes:
  main: Main path
steps:
- text: The session guest uses previous in the session.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product sends previous to the host and shows the host's new state.
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

# Go back on the host's music as a guest

## Trigger

The host lets guests control playback.

## Outcome

The host goes back for everyone following it.
