---
entities:
- entity: download
  shows:
  - Track
  - Progress
  - Origin
  - Added
  - Lyrics level
  - Waiting
- entity: saved-video
  shows:
  - Track
  - Progress
  - Status
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
- entity: preferences
  shows:
  - Downloads
- entity: lyrics
  shows:
  - Text
  - Source
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
---

# Downloads

Downloads, kept like a playlist: downloaded songs and saved music videos with their progress, size and saved lyrics, plus cancelling, retrying, removing and fetching missing lyrics.
