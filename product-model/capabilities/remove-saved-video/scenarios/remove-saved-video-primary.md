---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Remove downloaded video, or deletes all music videos in Downloads.
  kind: actor
  entities:
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product deletes the saved videos and keeps the songs downloaded.
  kind: product
  entities:
  - entity: saved-video
    effect: removes
  - entity: download
    effect: reads
    facts:
    - Track
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
  target: app/src/main/java/com/prism/music/download/Downloads.kt#removeVideo
---

# Remove a downloaded video

## Trigger

The listener wants a saved music video off the phone.

## Outcome

The video is deleted and the song stays downloaded.
