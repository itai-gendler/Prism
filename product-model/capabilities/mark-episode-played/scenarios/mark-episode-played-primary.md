---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Mark as played.
  kind: actor
  entities:
  - entity: episode
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
- text: The Product marks the episode played and forgets its position.
  kind: product
  entities:
  - entity: episode
    effect: changes
    from: Unplayed
    to: Played
    facts:
    - Position
  actor: listener
  contexts:
    main:
      place: phone::podcast
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/EpisodeProgress.kt
---

# Mark an episode as played

## Trigger

The listener has finished an episode elsewhere or wants it off Continue listening.

## Outcome

The episode shows as played and leaves Continue listening.
