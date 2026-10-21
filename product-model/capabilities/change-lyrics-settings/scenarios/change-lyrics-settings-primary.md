---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes lyric-source, timing, translation and car choices.
  kind: actor
  entities:
  - entity: preferences
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::lyrics-settings
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Lyrics
    - Translate lyrics
    - Translation language
    - Car lyrics
  actor: listener
  contexts:
    main:
      place: phone::lyrics-settings
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Lyrics settings

## Trigger

The listener opens Lyrics settings.

## Outcome

Lyric sources, timing preference, translation and car lyrics follow the new choices.
