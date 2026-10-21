---
kind: primary
routes:
  main: Main path
steps:
- text: The listener signs in with their Google account.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::sign-in
- text: The Product keeps the sign-in on this phone, finishes the welcome and starts syncing the library.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Signed in
    - Identity
    - Library sync
  actor: listener
  contexts:
    main:
      place: phone::sign-in
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LoginScreen.kt
---

# Sign in to YouTube Music

## Trigger

The listener wants their YouTube Music library in Prism.

## Outcome

Prism is signed in on this phone and starts syncing likes, playlists, albums and artists.

## Edge cases

- Leaving the Google sign-in before it finishes leaves Prism signed out.
- The account's name and picture can arrive after Prism has opened.
