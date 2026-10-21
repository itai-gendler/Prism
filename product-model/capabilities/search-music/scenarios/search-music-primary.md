---
kind: primary
routes:
  main: Main path
steps:
- text: The listener types a search.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::search
- text: The Product lists top results or the chosen kind of result and adds the search to Recent searches.
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
  - entity: album
    effect: reads
    facts:
    - Title
    - Artists
    - Release
    - Tracks
    - Artwork
    - Saved
    - Offline copy
  - entity: artist
    effect: reads
    facts:
    - Name
    - Artwork
    - Sections
    - Favourite
    - Channel
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
    effect: changes
    facts:
    - Recent searches
  actor: listener
  contexts:
    main:
      place: phone::search
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SearchScreen.kt
---

# Search music

## Trigger

The listener types in Search.

## Outcome

Top results, or the chosen kind of result, are listed as they type, and the search joins Recent searches.

## Edge cases

- Clearing the text clears the search.
- Offline, Search starts on the music on the phone.
