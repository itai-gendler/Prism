---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Stop updating it.
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
- text: The Product forgets the link to the playlist and leaves the playlist as it is.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Liked playlist
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::liked-songs
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LikedPlaylist.kt#stop
---

# Stop updating the Liked songs playlist

## Trigger

The listener no longer wants the playlist to follow their likes.

## Outcome

The playlist stays in the YouTube Music account but no longer changes; likes are untouched.
