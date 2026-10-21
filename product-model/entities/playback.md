---
singleton: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt
---

# Playback

The current listening session on this device.

## Information kept

- **Position** — Current playback position and known duration.
- **Media** — Current music or episode.
- **Mode** — Song audio or video.
- **Source details** — Downloaded, cached, local or streaming source and available codec and bitrate details.
- **Error** — Reported playback or video lookup failure.
- **Sleep timer** — A deadline, end-of-song pause or no timer.
- **Episode speed** — Playback speed applied to podcast episodes.
- **Output** — Requested audio output device.

## States

### Stopped

No active playback.

### Playing

Playback is running; loading may temporarily interrupt audible output.

### Paused

Playback is retained without advancing.
