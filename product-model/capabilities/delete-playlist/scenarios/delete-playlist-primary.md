---
kind: primary
routes:
  main: Main path
steps:
- text: The listener confirms deleting the playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product deletes the playlist, removes it from the library and drops any Home pin or Liked songs playlist link
    to it.
  kind: product
  entities:
  - entity: playlist
    effect: removes
  - entity: preferences
    effect: changes
    facts:
    - Pinned playlists
  - entity: account
    effect: changes
    facts:
    - Liked playlist
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#deletePlaylist
---

# Delete a playlist

## Trigger

The listener no longer wants one of their playlists.

## Outcome

The playlist is deleted from the YouTube Music account and leaves the library, Home pins and the Liked songs playlist link.

## Edge cases

- When YouTube Music refuses to delete a playlist the listener only saved, Prism removes it from the library instead.
- If both fail, the library shows the playlist again.
- The Liked songs playlist can also be deleted from Liked songs, after confirming; the songs stay liked.
