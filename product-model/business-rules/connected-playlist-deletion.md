---
appliesTo:
- type: entity
  id: playlist
  effect: removes
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
---

# Only a signed-in listener deletes playlists

The listener confirms first. When YouTube Music refuses to delete a playlist the listener saved, Prism removes it from the library instead.
