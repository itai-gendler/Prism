---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes choices in Library & Replay.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::library-replay
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Library
  actor: listener
  contexts:
    main:
      place: phone::library-replay
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Library & Replay settings

## Trigger

The listener opens Library & Replay settings.

## Outcome

The library and Replay follow the chosen preferences.
