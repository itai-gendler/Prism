---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens an artist.
  kind: actor
  entities:
  - entity: artist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::artist
- text: The Product shows the artist's picture, information, songs, releases, videos and similar artists.
  kind: product
  entities:
  - entity: artist
    effect: reads
    facts:
    - Name
    - Artwork
    - Sections
    - Favourite
    - Channel
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::artist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ArtistScreen.kt
---

# Browse an artist

## Trigger

The listener opens an artist.

## Outcome

The artist's picture, information, songs, releases, videos and similar artists are shown, with whether the artist is a favourite.
