---
kind: edge
routes:
  main: Main path
steps:
- text: An episode plays to within a minute of its known end.
  kind: condition
  entities:
  - entity: episode
    effect: reads
    facts: []
  - entity: playback
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::podcast
- text: The Product marks the episode played and forgets its position.
  kind: product
  entities:
  - entity: episode
    effect: changes
    from: In progress
    to: Played
    facts:
    - Position
    - Last heard
  contexts:
    main:
      place: phone::podcast
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt#playEpisode
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# An episode is heard to the end

## Trigger

An episode plays to within a minute of its end.

## Outcome

The episode is marked played and leaves Continue listening.
