---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener picks a song or Shuffle play in a media browser list.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::browse
- text: The Product queues the list from the chosen song, or shuffled.
  kind: product
  entities:
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Current
    - Order
    - Source
    - Shuffle
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
    facts:
    - Media
    - Position
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: android-media::browse
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/AppContainer.kt
---

# Play from the car

## Trigger

The listener picks a song or Shuffle play in Android Auto or another media browser.

## Outcome

The list plays from the chosen song, or as a new shuffled list.
