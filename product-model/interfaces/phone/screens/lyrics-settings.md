---
entities:
- entity: preferences
  shows: &id001
  - Lyrics
  - Translate lyrics
  - Translation language
  - Car lyrics
  collects: *id001
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
---

# Lyrics settings

The Lyrics settings page: lyric sources and their order, timing preference, translation and car lyrics.
