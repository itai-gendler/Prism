---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Tracks
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

# Only the signed-in owner takes songs out of a playlist

Prism offers removing a song only on the listener's own playlists while signed in.
