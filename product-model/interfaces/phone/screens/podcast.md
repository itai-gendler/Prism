---
entities:
- entity: podcast-show
  shows:
  - Title
  - Author
  - Description
  - Episodes
  - Saved
- entity: episode
  shows:
  - Title
  - Details
  - Position
  - Last heard
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
---

# Podcast

One podcast show: its description and episodes with each episode's progress, and saving the show to the library.
