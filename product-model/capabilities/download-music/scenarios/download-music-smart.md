---
kind: edge
routes:
  main: Main path
steps:
- text: Smart Downloads is on and Android lets its work run.
  kind: condition
  entities:
  - entity: download
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::downloads-storage
- text: The Product picks likely songs from recent plays, likes and recommendations, downloads a few at a time and gradually
    removes picks that no longer qualify.
  kind: product
  entities:
  - entity: preferences
    effect: reads
    facts:
    - Smart Downloads
    - Smart space
    - Smart mobile data
  - entity: download
    effect: creates
    to: Queued
    facts:
    - Track
    - Origin
    - Added
  - entity: song
    effect: reads
    facts: []
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

# Smart Downloads picks music ahead

## Trigger

Smart Downloads is on, and Android allows the work for the network, battery and storage.

## Outcome

Songs the listener is likely to play next are downloaded ahead, a few at a time, and older picks rotate out.

## Decision points

### Network

Which network may Smart Downloads use?

- Mobile data allowed → its picks download on any network.
- Mobile data not allowed → its picks wait for Wi-Fi.

### Space

How is the chosen space shared?

- Smart Downloads' picks → at most three quarters of it, leaving free space on the phone.
- Streamed music → the rest, with the least useful audio making way first.
