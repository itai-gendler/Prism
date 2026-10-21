---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Now playing.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product shows the current song or episode, its progress and source, the lyrics and the queue.
  kind: product
  entities:
  - entity: playback
    effect: reads
    facts:
    - Position
    - Media
    - Mode
    - Source details
    - Error
    - Sleep timer
    - Episode speed
    - Output
  - entity: queue
    effect: reads
    facts:
    - Entries
    - Current
    - Order
    - Source
    - Suggestions
    - Added by listener
    - Shuffle
    - Repeat
    - Saved position
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Duration
    - Artwork
    - Source
    - Liked
    - Not for me
    - Last played
  - entity: lyrics
    effect: reads
    facts:
    - Text
    - Timing
    - Source
    - Search name
    - Offset
    - Translation
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
  target: app/src/main/java/com/prism/music/ui/player/NowPlaying.kt
---

# Browse Now playing

## Trigger

The listener opens Now playing.

## Outcome

The current song, its progress and source, the lyrics and the queue are shown.
