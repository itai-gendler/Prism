---
kind: primary
routes:
  main: Main path
steps:
- text: The listener asks for a song's music video offline.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product downloads the song, the video's picture and, when it differs from the song, the video's own audio, and
    shows their combined progress.
  kind: product
  entities:
  - entity: download
    effect: creates
    to: Queued
    facts:
    - Track
    - Origin
    - Added
  - entity: saved-video
    effect: creates
    facts:
    - Track
    - Progress
    - Status
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#downloadVideo
---

# Download a music video

## Trigger

The listener wants a song's music video offline.

## Outcome

The video and the song download together, with one progress figure for the video.

## Edge cases

- When the song has no music video, Prism says there is none to download.
- Live streams cannot be downloaded as video.
