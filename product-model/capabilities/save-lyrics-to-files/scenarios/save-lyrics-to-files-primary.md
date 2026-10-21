---
kind: primary
routes:
  main: Main path
steps:
- text: The listener asks Prism to write lyric text into their music files and allows Android to let it change them.
  kind: actor
  entities:
  - entity: music-file
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::local-files
- text: The Product gets each song's lyrics and writes them into the supported files, then reports how many changed.
  kind: product
  entities:
  - entity: music-file
    effect: changes
    facts:
    - Embedded lyrics
  - entity: lyrics
    effect: reads
    facts:
    - Text
    - Timing
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::local-files
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/local/LyricsToFiles.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/components/LyricsToFilesHost.kt
---

# Save lyrics into music files

## Trigger

The listener wants other players to show the lyrics of their own music files.

## Outcome

Lyrics are written into the files' tags and Prism says how many files changed.

## Edge cases

- Unsupported files and files with no lyrics are skipped.
- At most 1,000 files are written in one go.
- Declining the Android request leaves the files unchanged.
- Songs Prism downloaded are not changed; only the listener's own files are.
