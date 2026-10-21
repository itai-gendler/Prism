---
kind: primary
routes:
  main: Main path
steps:
- text: The listener cancels the sleep timer.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product clears the timer.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Sleep timer
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Cancel the sleep timer

## Trigger

A sleep timer is set.

## Outcome

Playback carries on past the old time.
