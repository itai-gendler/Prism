---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener chooses Save in the queue and enters a name and visibility.
  kind: actor
  entities:
  - entity: queue
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product makes a playlist of the current and upcoming songs in play order, without repeats and at most 300, and
    reports whether it was made.
  kind: product
  entities:
  - entity: queue
    effect: reads
    facts:
    - Entries
    - Current
    - Order
    - Source
    - Suggestions
    - Added by listener
    - Shuffle
    - Repeat
    - Saved position
  - entity: playlist
    effect: creates
    facts:
    - Title
    - Visibility
    - Tracks
    - Owned
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
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

# Save the queue as a playlist

## Trigger

The listener wants to keep what is playing and what is up next.

## Outcome

A playlist of the current and upcoming songs in play order is made, without repeats and at most 300 songs.
