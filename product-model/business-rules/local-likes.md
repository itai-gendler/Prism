---
appliesTo:
- type: entity
  id: song
- type: capability
  id: update-liked-playlist
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/LibraryRepository.kt
---

# Likes of local files stay on the phone

Liking a file on the phone never likes anything on YouTube Music or starts a download, and the Liked songs playlist leaves such files out.
