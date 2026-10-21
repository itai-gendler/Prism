---
relations:
- entity: song
  verb: supplies
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/local/LocalMusic.kt
---

# Music file

An existing music file on the phone, indexed from Android media information and played in place without moving it.

## Information kept

- **Location** — The Android media location used to read the file.
- **Tags** — Title, artists, album, track number and year supplied by the file.
- **Format** — Audio format, size and duration.
- **Added** — When Android reports the file was added.
- **Embedded lyrics** — Lyrics written into supported FLAC or MP3 files.
- **Access** — Current Android read or write access relevant to this file.
