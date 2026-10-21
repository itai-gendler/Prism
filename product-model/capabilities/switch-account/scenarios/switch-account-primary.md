---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks another account or channel.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::account
- text: The Product switches to it, forgets the old account's likes, library lists and Liked songs playlist link, and syncs
    the new library.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Identity
    - Liked playlist
    - Library sync
  - entity: song
    effect: changes
    facts:
    - Liked
  - entity: playlist
    effect: changes
    facts:
    - Offline copy
  - entity: album
    effect: changes
    facts:
    - Offline copy
  - entity: listening-history
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::account
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt#switchAccount
---

# Switch account

## Trigger

The sign-in holds another account or brand channel.

## Outcome

Prism uses the chosen account; the old account's likes, library and Liked songs playlist link go, while likes of local files and Replay stay.
