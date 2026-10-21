---
entities:
- entity: preferences
  shows: &id001
  - Downloads
  - Smart Downloads
  - Smart space
  - Smart mobile data
  collects: *id001
- entity: download
  shows:
  - Track
  - Progress
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
---

# Downloads and storage

The Downloads & storage settings page: download networks, automatic downloads of liked songs, and Smart Downloads with its space and mobile-data choice.
