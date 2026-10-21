---
kind: primary
routes:
  main: Main path
steps:
- text: The listener chooses Get missing lyrics in Downloads.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  - entity: download
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::downloads
- text: The Product asks for lyrics for downloaded songs that lack them and saves what it finds.
  kind: product
  entities:
  - entity: download
    effect: changes
    facts:
    - Lyrics level
  - entity: lyrics
    effect: changes
    facts:
    - Text
    - Timing
    - Source
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
  target: app/src/main/java/com/prism/music/download/Downloads.kt#backfillLyrics
---

# Get missing lyrics for downloads

## Trigger

Some downloaded songs have no lyrics, or only untimed ones.

## Outcome

Downloads shows the songs' improved lyric levels where lyrics were found.

## Edge cases

- A song no source has lyrics for stays downloaded without them.
- Prism also fetches missing lyrics by itself, respecting Wi-Fi only and waiting between attempts; Get missing lyrics asks again straight away.
