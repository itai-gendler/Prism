---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Saved
  contexts:
  - place: phone::playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
---

# Only a signed-in listener saves or removes playlists in the library

Saving and removing go to the YouTube Music account; the library changes once YouTube Music accepts them.
