---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Tracks
  contexts:
  - place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/components/Components.kt
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
---

# Only a signed-in listener adds songs to playlists

Songs are added in the YouTube Music account, and Prism says when an addition is refused.
