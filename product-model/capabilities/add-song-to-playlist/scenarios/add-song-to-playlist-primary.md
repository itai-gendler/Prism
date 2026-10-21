---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks one of their playlists from the searchable list for the selected song.
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
      place: phone::player
- text: The Product adds the song to that playlist in the YouTube Music account and reports whether it was added.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Source
  - entity: playlist
    effect: changes
    facts:
    - Tracks
  - entity: account
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/components/Components.kt#PlaylistPicker
---

# Add a song to one of the listener's playlists

## Trigger

The listener wants a song in one of their YouTube Music playlists.

## Outcome

The song is added to the chosen playlist, or the listener is told it could not be added.

## Edge cases

- Files on the phone cannot be added to YouTube Music playlists.
- From the same list, the listener can make a new playlist with the song already in it.
