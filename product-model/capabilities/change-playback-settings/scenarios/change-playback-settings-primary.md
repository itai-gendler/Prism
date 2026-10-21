---
kind: primary
routes:
  main: Main path
steps:
- text: The listener changes sound, quality and video choices.
  kind: actor
  entities:
  - entity: preferences
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playback-sound
- text: The Product keeps the choices on this phone and applies them.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Playback
  actor: listener
  contexts:
    main:
      place: phone::playback-sound
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/prefs/Settings.kt
---

# Change Playback & sound settings

## Trigger

The listener opens Playback & sound.

## Outcome

Quality, lossless, normalization, spatial audio, crossfade and music video choices apply to what plays next.

## Decision points

### Crossfade

How does one song run into the next?

- Crossfade off, or a pair crossfade leaves alone → the next song simply follows.
- Crossfade on for a pair it applies to → the songs fade into each other over the chosen length, or a length worked out for the pair, and match tempo and beats when that is on.

### Data saver

What does data saver change?

- On mobile data with data saver on → songs play at the mobile data quality and at most Normal, music videos at 480p at most, and pictures are fetched smaller or not at all.
- On Wi-Fi, or with data saver off → the chosen qualities apply.
