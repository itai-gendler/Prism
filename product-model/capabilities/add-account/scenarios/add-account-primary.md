---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Add a Google account and completes the Google sign-in.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::account
- text: The Product keeps the added account with the existing sign-in and offers it under Switch account.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Signed in
  actor: listener
  contexts:
    main:
      place: phone::account
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LoginScreen.kt
---

# Add another Google account

## Trigger

The listener wants a second Google account or a brand channel available in Prism.

## Outcome

The added account is kept on this phone and can be chosen with Switch account.
