---
appliesTo:
- type: entity
  id: music-file
  effect: changes
  facts:
  - Embedded lyrics
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/components/LyricsToFilesHost.kt
permits:
- actors:
  - listener
  when:
  - fact: Access
    is: Write allowed
---

# Lyrics are written into files only with Android's permission

Prism asks Android for permission to change the files, for each batch where Android requires it, before writing lyrics.
