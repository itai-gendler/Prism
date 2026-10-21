---
kind: validation
routes:
  main: Main path
steps:
- text: The listener opens the Liked songs playlist while not signed in.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::liked-songs
  actor: listener
- text: The Product asks the listener to sign in to YouTube Music first.
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Signed in
  contexts:
    main:
      place: phone::liked-songs
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LikedPlaylistSheet.kt
---

# The Liked songs playlist needs an account

## Trigger

The listener is not signed in.

## Outcome

The listener is asked to sign in to YouTube Music, and no playlist is made.
