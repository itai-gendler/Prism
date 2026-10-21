---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Radio.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product starts a radio queue from it, leaving out songs already queued and songs marked Not for me.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Source
    - Suggestions
  - entity: song
    effect: reads
    facts:
    - Not for me
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
    facts:
    - Media
    - Position
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# Start radio

## Trigger

The listener wants more music like a song, album, playlist or artist.

## Outcome

A radio queue plays, without songs already queued or marked Not for me.
