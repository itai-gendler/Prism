---
kind: primary
routes:
  main: Main path
steps:
- text: The listener plays music.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product replaces the queue with the selection and starts playing.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Order
    - Source
    - Suggestions
    - Added by listener
    - Shuffle
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
    facts:
    - Media
    - Position
    - Mode
    - Source details
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
  target: app/src/main/java/com/prism/music/AppContainer.kt
---

# Play music

## Trigger

The listener plays a song, album, playlist or list.

## Outcome

The selection replaces the queue and starts playing from the chosen song.

## Edge cases

- An empty selection leaves the current queue intact.
- Which streams and formats are available is up to YouTube Music.
