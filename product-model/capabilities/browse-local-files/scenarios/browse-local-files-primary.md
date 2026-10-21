---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Local files.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::local-files
- text: The Product lists the phone's music files of at least twenty seconds by their tags and artwork, in the chosen section.
  kind: product
  entities:
  - entity: music-file
    effect: changes
    facts:
    - Location
    - Tags
    - Format
    - Added
    - Access
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
    - Album
    - Duration
    - Artwork
    - Source
    - Liked
    - Not for me
    - Last played
  actor: listener
  contexts:
    main:
      place: phone::local-files
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/local/LocalMusic.kt#scan
---

# Browse local files

## Trigger

The listener has allowed Prism to read the phone's audio.

## Outcome

The music files on the phone are listed by song, album or artist in the sections the listener chose.

## Edge cases

- With permission but no music files, Local files says it found none rather than asking for permission.
- Files added or removed are picked up shortly after Android notices them.
