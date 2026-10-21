---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Sync with YouTube Music in Library.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::library
- text: The Product brings in the account's likes, playlists, albums and artists, keeps likes of local files and saves the
    lists for offline.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Library sync
    - Identity
  - entity: song
    effect: changes
    facts:
    - Liked
  - entity: playlist
    effect: changes
    facts:
    - Title
    - Tracks
    - Saved
    - Offline copy
  - entity: album
    effect: changes
    facts:
    - Saved
    - Offline copy
  - entity: artist
    effect: changes
    facts:
    - Name
    - Artwork
  actor: listener
  contexts:
    main:
      place: phone::library
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#sync
---

# Sync the library

## Trigger

The listener asks for a sync, or opens Prism or Library while signed in.

## Outcome

Likes, playlists, albums and artists match the YouTube Music account and are kept for offline browsing; likes of local files stay.
