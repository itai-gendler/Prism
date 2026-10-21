---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/model/Models.kt
---

# Song

A music track Prism identifies across discovery, playback, likes and listening history. Its source can be the catalog or a file on this phone.

## Information kept

- **Title** — Track name.
- **Artists** — Performing artists and any catalog links.
- **Album** — Album name and any catalog link.
- **Duration** — Known track length.
- **Artwork** — Available cover image.
- **Source** — Catalog audio, music video, live stream or local file.
- **Liked** — Whether the track is liked on this phone and when it was liked.
- **Not for me** — Whether recommendations should avoid this track.
- **Last played** — Most recent playback on this device.
