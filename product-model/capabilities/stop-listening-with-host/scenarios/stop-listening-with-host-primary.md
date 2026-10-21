---
kind: primary
routes:
  main: Main path
steps:
- text: The session guest turns off Play here too.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product stops following the host on this phone and keeps the guest in the session.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - Play here too
  - entity: playback
    effect: reads
    facts: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#setListenHere
---

# Stop playing the host's music on this phone

## Trigger

A guest wants only to add songs, not listen on their own phone.

## Outcome

The phone stops following the host and the guest stays in the session.
