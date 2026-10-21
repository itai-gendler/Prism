---
kind: primary
routes:
  main: Main path
steps:
- text: The session host turns Guests can control playback on or off.
  kind: actor
  entities:
  - entity: playback
    effect: reads
    facts: []
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
- text: The Product keeps the choice and tells the connected guests.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - Guest control
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#setGuestsControl
---

# Let guests control playback

## Trigger

The host is running a session.

## Outcome

Guests can, or can no longer, play, pause, skip and seek the host's music.
