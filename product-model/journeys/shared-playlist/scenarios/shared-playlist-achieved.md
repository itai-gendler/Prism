---
kind: primary
result: achieved
routes:
  main: Android app
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
  capability: open-prism-link
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
  capability: open-prism-link
- text: The listener browses the playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Description
    - Visibility
    - Tracks
  actor: listener
  contexts:
    main:
      place: phone::playlist
  capability: browse-playlist
---

# Open a shared playlist link

## Trigger

Someone shared a YouTube Music playlist link with the listener.

## Outcome

The playlist is open in Prism.
