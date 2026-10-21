---
availability:
- place: phone
- place: android-media
- place: voice
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/AppContainer.kt
domain: player
---

# Play music

Play a song, album, playlist or list from the chosen song, or shuffled. Prism plays from a file on the phone, a download or saved audio when it has one, otherwise streams.
