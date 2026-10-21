---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes choices in Player settings.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player-settings
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Player
  actor: listener
  contexts:
    main:
      place: phone::player-settings
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Player settings

## Trigger

The listener opens Player settings.

## Outcome

The player looks and behaves as chosen.
