---
kind: primary
routes:
  main: Main path
steps:
- text: The listener plays or continues an episode.
  kind: actor
  entities:
  - entity: episode
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::podcast
- text: The Product starts the episode from its saved position, if any, at the episode speed.
  kind: product
  entities:
  - entity: episode
    effect: reads
    facts:
    - Title
    - Position
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Source
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
    facts:
    - Media
    - Position
    - Episode speed
  actor: listener
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

# Play a podcast episode

## Trigger

The listener plays an episode.

## Outcome

The episode starts where the listener left off, at the chosen episode speed, without music autoplay.
