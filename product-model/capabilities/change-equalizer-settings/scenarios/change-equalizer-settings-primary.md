---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes the equalizer.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::equalizer
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Equalizer
  actor: listener
  contexts:
    main:
      place: phone::equalizer
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/EqualizerScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Equalizer settings

## Trigger

The listener opens the equalizer.

## Outcome

The chosen preset, bands, bass boost and loudness apply to what plays and stay on this phone.
