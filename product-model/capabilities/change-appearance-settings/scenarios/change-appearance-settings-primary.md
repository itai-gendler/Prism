---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes choices in Appearance.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::appearance
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Appearance
  actor: listener
  contexts:
    main:
      place: phone::appearance
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Appearance settings

## Trigger

The listener opens Appearance.

## Outcome

The chosen theme, fonts and presentation take effect and stay on this phone.
