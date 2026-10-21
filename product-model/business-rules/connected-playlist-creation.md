---
appliesTo:
- type: entity
  id: playlist
  effect: creates
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
---

# Only a signed-in listener creates playlists

Playlists are made in the YouTube Music account; a playlist exists in Prism only once YouTube Music has made it.
