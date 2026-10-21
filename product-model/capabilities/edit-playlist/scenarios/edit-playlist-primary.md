---
kind: primary
routes:
  main: Main path
steps:
- text: The listener saves a new title, description or visibility.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::playlist
- text: The Product sends the changes and shows them once they are accepted; a blank title keeps the old one.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Title
    - Description
    - Visibility
  actor: listener
  contexts:
    main:
      place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Edit playlist details

## Trigger

The listener edits one of their own playlists.

## Outcome

The playlist shows the new title, description or visibility once YouTube Music accepts them.

## Edge cases

- When saving fails, the previous details stay.
