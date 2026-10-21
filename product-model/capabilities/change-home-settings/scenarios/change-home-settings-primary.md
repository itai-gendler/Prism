---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes choices in Home screen settings.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::home-settings
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Home
  actor: listener
  contexts:
    main:
      place: phone::home-settings
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CatalogueScreen.kt
---

# Change Home screen settings

## Trigger

The listener opens Home screen settings.

## Outcome

Home shows the chosen greeting, shortcuts and sections in the chosen order.
