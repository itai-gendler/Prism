---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses and orders the Local files sections.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::local-files
- text: The Product keeps the choice on this phone and applies it.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Local sections
  actor: listener
  contexts:
    main:
      place: phone::local-files
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LocalMusicScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Choose Local files sections

## Trigger

The listener edits the sections of Local files.

## Outcome

Local files offers the chosen sections in the chosen order.
