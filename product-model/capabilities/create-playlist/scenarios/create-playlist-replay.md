---
kind: alternate
routes:
  main: Android app
steps:
- text: The listener chooses to save the period's top songs to YouTube Music.
  kind: actor
  entities:
  - entity: listening-history
    effect: reads
    facts:
    - Music
    - Time heard
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::replay
  actor: listener
- text: The Product makes a playlist named for the period with its top 100 songs.
  kind: product
  entities:
  - entity: playlist
    effect: creates
    facts:
    - Title
    - Description
    - Tracks
    - Owned
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::replay
  actor: listener
- text: The Product opens the new playlist.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Tracks
  contexts:
    main:
      place: phone::playlist
  actor: listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ReplayScreen.kt
---

# Save Replay as a playlist

## Trigger

The listener wants a period's top songs as a playlist.

## Outcome

A playlist of the period's top 100 songs is made in the YouTube Music account and opens.
