---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Update now.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::liked-songs
- text: The Product reads the playlist back, adds new likes, removes unliked songs and records the update time.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Liked
    - Source
  - entity: playlist
    effect: changes
    facts:
    - Tracks
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
  target: app/src/main/java/com/prism/music/data/LikedPlaylist.kt#sync
---

# Update the Liked songs playlist now

## Trigger

The listener wants the playlist in line with their likes right away.

## Outcome

The playlist matches the liked catalog songs, including changes made to it outside Prism, and shows when it was updated.

## Edge cases

- While no likes have loaded, Prism leaves the playlist as it is rather than emptying it.
- When an update fails, the Liked songs playlist shows the error.
