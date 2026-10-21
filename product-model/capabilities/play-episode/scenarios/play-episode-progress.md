---
kind: edge
routes:
  main: Main path
steps:
- text: An episode plays, pauses or changes.
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
- text: The Product keeps the position once past thirty seconds, for up to fifty unfinished episodes, most recently heard
    first.
  kind: product
  entities:
  - entity: episode
    effect: changes
    from: Unplayed
    to: In progress
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

# Episode progress is kept

## Trigger

An episode has played for more than thirty seconds.

## Outcome

The episode is in Continue listening with its position, most recently heard first, up to fifty episodes.
