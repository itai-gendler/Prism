---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Offline copy
  contexts:
  - place: phone::library
  - place: phone::account
- type: entity
  id: album
  effect: changes
  facts:
  - Offline copy
  contexts:
  - place: phone::library
  - place: phone::account
permits:
- actors:
  - listener
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# The listener's account decides which playlists and albums are kept for offline

Syncing saves the account's playlists and albums for offline browsing; switching account and signing out remove them from the phone.
