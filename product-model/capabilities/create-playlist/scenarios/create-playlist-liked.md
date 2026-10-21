---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener enters a name and visibility and confirms.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::liked-songs
- text: The Product makes the playlist from the liked catalog songs, oldest like first, adding them in batches, and remembers
    it as the Liked songs playlist.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Liked
    - Source
  - entity: playlist
    effect: creates
    facts:
    - Title
    - Description
    - Visibility
    - Tracks
    - Owned
  - entity: account
    effect: changes
    facts:
    - Liked playlist
  actor: listener
  contexts:
    main:
      place: phone::liked-songs
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerQueue.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LikedPlaylist.kt
---

# Make the Liked songs playlist

## Trigger

The listener wants their likes as a playlist they can share, pin or open in other apps.

## Outcome

A playlist of every liked catalog song, oldest like first, is made and kept up to date from then on.
