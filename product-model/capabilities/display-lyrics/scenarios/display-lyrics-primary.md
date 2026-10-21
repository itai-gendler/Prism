---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens the lyrics.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product shows the chosen or best lyrics and follows playback with their word or line timing.
  kind: product
  entities:
  - entity: lyrics
    effect: changes
    facts:
    - Text
    - Timing
    - Source
  - entity: playback
    effect: reads
    facts:
    - Position
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/lyrics/Lyrics.kt#auto
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt
---

# Show lyrics

## Trigger

The listener opens the lyrics for the current song.

## Outcome

The lyrics follow the song, word by word or line by line when timed, otherwise as plain text.

## Edge cases

- Podcast episodes have no lyrics.
- Saved lyrics show without a network.
