---
kind: alternate
result: achieved
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
  capability: create-playlist
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
  capability: create-playlist
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
  capability: create-playlist
- text: The listener browses the new playlist.
  kind: actor
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
  capability: browse-playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ReplayScreen.kt
---

# Save Replay as a playlist and land in it

## Trigger

The listener chooses Save as a playlist in Replay.

## Outcome

The playlist of the period's top songs is open and the listener is in it.
