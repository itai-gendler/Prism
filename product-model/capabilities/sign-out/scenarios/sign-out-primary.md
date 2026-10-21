---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Sign out.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::account
- text: The Product forgets the sign-in and removes the account's library lists and their offline copies.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Signed in
    - Identity
    - Library sync
  - entity: playlist
    effect: changes
    facts:
    - Offline copy
  - entity: album
    effect: changes
    facts:
    - Offline copy
  actor: listener
  contexts:
    main:
      place: phone::account
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# Sign out

## Trigger

The listener no longer wants their account in Prism.

## Outcome

Prism is signed out, and the account's library lists and offline copies of its playlists and albums leave the phone.
