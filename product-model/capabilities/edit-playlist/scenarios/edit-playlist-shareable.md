---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener chooses Make unlisted in the share sheet.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product makes the playlist unlisted and updates the sharing notice once YouTube Music accepts it.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Visibility
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Make a private playlist unlisted to share it

## Trigger

The listener shares one of their own private playlists, whose link would only work for them.

## Outcome

The playlist becomes unlisted, so its link works for others.
