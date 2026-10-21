---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Title
  - Tracks
  - Saved
  contexts:
  - place: phone::library
- type: entity
  id: album
  effect: changes
  facts:
  - Saved
  contexts:
  - place: phone::library
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# Only a signed-in listener syncs the library

Syncing reads the YouTube Music account and updates the library's lists on the phone.
