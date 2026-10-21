---
kind: edge
routes:
  main: Main path
steps:
- text: Likes change while the Liked songs playlist is set up.
  kind: condition
  entities:
  - entity: playlist
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::liked-songs
- text: The Product brings the playlist in line with the liked catalog songs and records when it did.
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
  contexts:
    main:
      place: phone::liked-songs
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LikedPlaylist.kt#sync
---

# The Liked songs playlist follows likes

## Trigger

The listener likes or unlikes songs while the Liked songs playlist is set up.

## Outcome

A few seconds later the playlist has the new likes added and the unliked songs removed.
