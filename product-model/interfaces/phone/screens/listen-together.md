---
entities:
- entity: together-session
  shows:
  - Host
  - Code
  - Guests
  - Guest control
  - Now playing
  - Play here too
  - In step
  - Connection
- entity: song
  shows:
  - Title
  - Artists
  - Album
  - Duration
  - Artwork
  - Liked
  - Not for me
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
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/TogetherScreen.kt
---

# Listen together

Listen together: start a session or find one nearby; inside one, who is listening, what is playing and up next, and the host's or guest's controls.
