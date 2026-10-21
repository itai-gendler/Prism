---
kind: primary
routes:
  main: Main path
steps:
- text: The listener asks for the current lyric text again.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product fetches the lyrics again and keeps the earlier lyrics if that fails.
  kind: product
  entities:
  - entity: lyrics
    effect: changes
    facts:
    - Text
    - Timing
    - Source
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt#redownload
---

# Re-download lyrics

## Trigger

The listener wants fresh lyrics for the current song.

## Outcome

The lyrics are fetched again; if that fails, the lyrics already found stay.
