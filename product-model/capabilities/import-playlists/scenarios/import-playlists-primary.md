---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses where the playlists come from.
  kind: actor
  entities:
  - entity: playlist
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::import
- text: The Product opens the transfer service and syncs the library when the listener comes back, without sharing Prism's
    YouTube Music sign-in.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Library sync
  actor: listener
  contexts:
    main:
      place: phone::import
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ImportScreen.kt
---

# Import playlists

## Trigger

The listener wants playlists from another service in their library.

## Outcome

The transfer continues on the transfer service; when the listener comes back, Prism syncs the library to bring the imported playlists in.

## Edge cases

- A transfer that is cancelled or fails on the transfer service brings no new playlists.
