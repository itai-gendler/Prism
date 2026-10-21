---
singleton: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlayerConnection.kt
---

# Queue

The ordered music selected for playback, including the current entry, played history and upcoming suggestions.

## Information kept

- **Entries** — Music in the queue, including repeated selections where supported.
- **Current** — The current entry.
- **Manual arrangement** — The listener’s explicitly arranged upcoming sequence.
- **Order** — The sequence that will actually play and the already played sequence.
- **Source** — Where playback began and its displayed title.
- **Suggestions** — Where autoplay additions begin and the outstanding continuation.
- **Added by listener** — Selections explicitly added with Play next or Add to queue.
- **Shuffle** — Whether playback follows a newly shuffled order.
- **Repeat** — Off, all or one.
- **Saved position** — Last persisted queue position for playback resumption.
