---
kind: validation
routes:
  main: Android app
steps:
- text: The listener picks a song with no offline audio while offline.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::album
  actor: listener
- text: The Product says the song is not available offline and leaves the queue as it was.
  kind: product
  entities:
  - entity: queue
    effect: reads
    facts:
    - Entries
    - Current
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::album
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# A song that is not downloaded

## Trigger

The listener is offline and picks a song in a saved collection that has no offline audio.

## Outcome

Prism says the song is not downloaded and the current queue stays as it was.
