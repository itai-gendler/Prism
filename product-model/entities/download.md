---
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt
---

# Download

A song kept for offline listening in Downloads: one Prism downloaded, or a lossless file already on the phone that matches a catalog song.

## Information kept

- **Track** — Music or episode the entry represents.
- **Progress** — Completed bytes and reported percent.
- **Origin** — Manual download, Smart Downloads pick or matched local lossless file.
- **Added** — When the entry was added.
- **Lyrics level** — None, plain, line-synced or word-synced lyrics currently saved.
- **Waiting** — The network requirement currently holding queued work.

## States

### Queued

An audio download has been requested.

### Downloading

Audio bytes are being received.

### Completed

The audio is saved or a matched lossless file is available.

### Failed

The download failed and can be retried.
