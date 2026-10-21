---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Title
  - Description
  - Visibility
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
  - fact: Owned
    is: true
---

# Only the signed-in owner edits a playlist's details

Title, description and visibility can be edited only on the listener's own playlists while signed in. The change counts once YouTube Music accepts it.
