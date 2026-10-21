---
singleton: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# YouTube Music account

The YouTube Music sign-in Prism keeps on this phone. The account itself, and the library it holds, belong to YouTube Music.

## Information kept

- **Signed in** — Whether Prism has a saved YouTube Music session.
- **Identity** — Selected account or channel, name, email or byline and avatar.
- **Library sync** — Idle, syncing, done or error, with the last error when one is reported.
- **Liked playlist** — The Liked songs playlist Prism keeps up to date, if one is set up: its name, last update and last error.
