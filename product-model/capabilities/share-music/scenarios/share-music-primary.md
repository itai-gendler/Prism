---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses to share a link, text or a story card.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product prepares it and hands it to Android sharing or copies the link.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Artwork
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Picture
    - Tracks
  - entity: album
    effect: reads
    facts:
    - Title
    - Artists
    - Artwork
  - entity: artist
    effect: reads
    facts:
    - Name
    - Artwork
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/components/ShareSheet.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/ShareLinks.kt
---

# Share music

## Trigger

The listener wants to share a song, album, playlist or artist.

## Outcome

A link or a story card made from the artwork is handed to Android sharing, or the link is copied.

## Edge cases

- If the story card cannot be made, Prism says so.
- Liked songs and Downloads have no link of their own to share.
