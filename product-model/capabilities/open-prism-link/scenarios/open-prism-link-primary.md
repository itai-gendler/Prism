---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens a playlist link with Prism.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::home
- text: The Product opens the playlist.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Description
    - Tracks
    - Picture
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/MainActivity.kt#handleDeepLink
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/ShareLinks.kt#findIn
---

# Open a shared playlist

## Trigger

The listener opens or shares a YouTube Music playlist link to Prism.

## Outcome

The playlist opens in Prism.
