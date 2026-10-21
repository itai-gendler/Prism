---
kind: edge
routes:
  main: Main path
steps:
- text: The listener reads lyrics with translation on.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
  actor: listener
- text: The Product keeps showing the original lyrics when the translation fails.
  kind: product
  entities:
  - entity: lyrics
    effect: reads
    facts:
    - Text
    - Translation
  contexts:
    main:
      place: phone::player
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/lyrics/LyricsTranslator.kt
---

# Lyrics cannot be translated

## Trigger

Translation is on but the translation does not come back usable.

## Outcome

The original lyrics stay on screen.
