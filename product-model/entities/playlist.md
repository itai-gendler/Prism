---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Playlist

A YouTube Music playlist displayed and edited through Prism, with an optional picture chosen only on this phone.

## Information kept

- **Title** — Playlist name.
- **Description** — Optional description.
- **Visibility** — Private, unlisted or public value returned by or sent to YouTube Music.
- **Tracks** — The displayed ordered tracks and available removal slots.
- **Owned** — Whether the returned playlist page identifies it as owned.
- **Saved** — Whether the playlist is saved in the connected library.
- **Picture** — Catalog artwork or a local picture override.
- **Offline copy** — The last saved playlist details and tracks.
