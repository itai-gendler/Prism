---
kind: primary
routes:
  main: Main path
steps:
- text: The listener confirms removing the chosen downloads.
  kind: actor
  entities:
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product deletes the downloaded audio and saved videos, and only hides lossless files from the phone's own music.
  kind: product
  entities:
  - entity: download
    effect: removes
    from: Completed
  - entity: saved-video
    effect: removes
  actor: listener
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#removeMany
---

# Remove downloads

## Trigger

The listener wants downloaded songs off the phone.

## Outcome

The chosen downloads and their saved videos are deleted; a lossless file from the phone only leaves the list and stays on the phone.
