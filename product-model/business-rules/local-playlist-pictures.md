---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Picture
permits:
- actors:
  - listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/PlaylistCovers.kt
---

# Playlist pictures the listener picks stay on the phone

A picture chosen for a playlist, Liked songs or Downloads is shown only in Prism on this phone and does not change the playlist on YouTube Music.
