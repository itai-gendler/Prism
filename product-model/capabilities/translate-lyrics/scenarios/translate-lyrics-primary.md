---
kind: primary
routes:
  main: Main path
steps:
- text: The listener reads lyrics with translation on.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product has the lyric text translated and shows each line's translation when the language differs.
  kind: product
  entities:
  - entity: lyrics
    effect: changes
    facts:
    - Translation
  - entity: preferences
    effect: reads
    facts:
    - Translate lyrics
    - Translation language
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/lyrics/LyricsTranslator.kt
---

# Translate lyrics

## Trigger

Translation is on and the lyrics are in another language.

## Outcome

A translation shows under each line in the chosen language.

## Edge cases

- Translation failure leaves the original lyrics usable.
- Lyrics already in the chosen language get no translation.
