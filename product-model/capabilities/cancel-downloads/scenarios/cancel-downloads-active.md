---
kind: alternate
routes:
  main: Main path
steps:
- text: The listener cancels a song that is still downloading.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product stops the download and removes it.
  kind: product
  entities:
  - entity: download
    effect: removes
    from: Downloading
  actor: listener
  contexts:
    main:
      place: phone::downloads
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt#DownloadsInfo
---

# Cancel a download in progress

## Trigger

A song is still downloading.

## Outcome

The download stops and leaves Downloads.
