---
appliesTo:
- type: entity
  id: music-file
  effect: changes
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/local/LocalMusic.kt#scan
permits:
- actors:
  - listener
  when:
  - entity: preferences
    fact: Music access
    is: true
---

# Local files need Android's permission to read audio

Prism asks for Android's audio permission and lists the phone's music only once it is granted.
