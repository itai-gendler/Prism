---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes choices in Downloads & storage.
  kind: actor
  entities:
  - entity: preferences
    effect: reads
    facts: []
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads-storage
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Downloads
    - Smart Downloads
    - Smart space
    - Smart mobile data
  actor: listener
  contexts:
    main:
      place: phone::downloads-storage
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Downloads & storage settings

## Trigger

The listener opens Downloads & storage.

## Outcome

The chosen download network, automatic downloads and Smart Downloads choices take effect and stay on this phone.
