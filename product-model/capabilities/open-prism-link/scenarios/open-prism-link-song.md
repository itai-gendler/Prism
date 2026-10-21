---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener shares a song link to Prism.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product opens the player and plays the song.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Source
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
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/MainActivity.kt#handleDeepLink
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/ShareLinks.kt#findIn
---

# Open a shared song

## Trigger

The listener shares a YouTube or YouTube Music song link to Prism from another app.

## Outcome

The song plays in Prism.
