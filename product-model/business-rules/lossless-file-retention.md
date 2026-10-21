---
appliesTo:
- type: entity
  id: download
- type: entity
  id: music-file
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#remove
---

# Removing a lossless file from Downloads keeps the file

A lossless file from the phone that appears in Downloads is only hidden from the list when removed; Prism never deletes the listener's own file this way.
