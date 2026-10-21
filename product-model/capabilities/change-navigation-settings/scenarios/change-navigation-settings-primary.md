---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes choices in Layout & navigation.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::layout-navigation
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Navigation
  actor: listener
  contexts:
    main:
      place: phone::layout-navigation
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Layout & navigation settings

## Trigger

The listener opens Layout & navigation.

## Outcome

The start tab, bottom-bar tabs and mini player follow the new choices.
