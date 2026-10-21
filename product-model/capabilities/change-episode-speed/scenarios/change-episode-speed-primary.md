---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks an episode speed.
  kind: actor
  entities:
  - entity: episode
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product keeps the speed and plays episodes at it.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Episode speed
  - entity: episode
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt#setEpisodeSpeed
---

# Change episode speed

## Trigger

An episode is playing.

## Outcome

Episodes play at the chosen speed, from 0.75 to 2 times; music still plays at normal speed.
