---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Mark as unplayed.
  kind: actor
  entities:
  - entity: episode
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
- text: The Product clears the played mark and any saved position.
  kind: product
  entities:
  - entity: episode
    effect: changes
    from: Played
    to: Unplayed
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

# Mark an episode as unplayed

## Trigger

The listener wants to hear a played episode again.

## Outcome

The episode shows as unplayed and starts from the beginning.
