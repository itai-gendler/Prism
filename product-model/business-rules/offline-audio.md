---
appliesTo:
- type: capability
  id: play-music
- type: capability
  id: browse-album
- type: capability
  id: browse-playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/AppContainer.kt#availableOffline
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt#orSaved
---

# A saved playlist or album plays offline only where its songs have offline audio

Saved details let the listener browse a playlist or album offline. A song plays offline only from a file on the phone, a finished download or audio saved whole while streaming.
