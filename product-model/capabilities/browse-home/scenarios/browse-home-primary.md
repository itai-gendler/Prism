---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens or refreshes Home.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::home
- text: The Product shows the catalog shelves, Quick picks, shortcuts and pinned playlists.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Duration
    - Artwork
    - Source
    - Liked
    - Not for me
    - Last played
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Description
    - Visibility
    - Tracks
    - Owned
    - Saved
    - Picture
    - Offline copy
  - entity: preferences
    effect: reads
    facts:
    - Home
    - Pinned playlists
  actor: listener
  contexts:
    main:
      place: phone::home
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/HomeScreen.kt
---

# Browse Home

## Trigger

The listener opens or refreshes Home.

## Outcome

Home shows the catalog shelves, Quick picks, Speed dial, shortcuts and pinned playlists.

## Edge cases

- When a refresh brings no Quick picks, the previous ones stay for the rest of the session.
