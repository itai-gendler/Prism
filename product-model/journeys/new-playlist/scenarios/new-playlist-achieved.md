---
kind: primary
result: achieved
routes:
  main: Android app
steps:
- text: The listener enters a name and visibility for a new playlist in Library.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::library
  capability: create-playlist
- text: The Product makes the playlist and opens it.
  kind: product
  entities:
  - entity: playlist
    effect: creates
    facts:
    - Title
    - Visibility
    - Owned
  actor: listener
  contexts:
    main:
      place: phone::playlist
  capability: create-playlist
- text: The listener browses the new playlist.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Title
    - Description
    - Visibility
    - Tracks
  actor: listener
  contexts:
    main:
      place: phone::playlist
  capability: browse-playlist
---

# Create a playlist in Library and land in it

## Trigger

The listener creates a playlist in Library.

## Outcome

The new playlist is open and the listener is in it.
