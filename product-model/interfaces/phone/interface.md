---
type: mobile-app
actors:
- listener
- session-host
- session-guest
entryPoints:
- mobile-app: https://music.youtube.com/
languages:
- en
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/MainActivity.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/Nav.kt
---

# Android app

The listener uses Prism on an Android phone, with optional YouTube Music sign-in. The same listening places remain available without an account; account operations and session responsibilities have their own conditions.
