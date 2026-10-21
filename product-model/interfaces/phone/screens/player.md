---
entities:
- entity: playback
  shows:
  - Position
  - Media
  - Mode
  - Source details
  - Error
  - Sleep timer
  - Episode speed
  - Output
- entity: queue
  shows:
  - Entries
  - Current
  - Order
  - Source
  - Suggestions
  - Added by listener
  - Shuffle
  - Repeat
  - Manual arrangement
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
- entity: episode
  shows:
  - Title
  - Details
  - Position
  - Last heard
- entity: lyrics
  shows:
  - Text
  - Timing
  - Source
  - Search name
  - Offset
  - Translation
- entity: preferences
  shows:
  - Autoplay
- entity: playlist
  shows:
  - Title
  - Picture
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/NowPlaying.kt
---

# Now playing

Now playing: the current song, episode or video with its progress and source, lyrics, the queue with what was played and what is up next, and the sleep timer.
