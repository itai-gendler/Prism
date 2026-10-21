---
appliesTo:
- type: entity
  id: playlist
  effect: changes
  facts:
  - Tracks
  contexts:
  - place: phone::liked-songs
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LikedPlaylist.kt
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
- unattended: true
  when:
  - entity: account
    fact: Signed in
    is: true
---

# The Liked songs playlist is kept up to date only while signed in

Updating the playlist, whether the listener asks or likes change, needs the YouTube Music account. Stopping the updates forgets the link to the playlist and leaves it as it is.
