---
kind: primary
routes:
  main: Main path
steps:
- text: The listener enters another title and, optionally, performer to look the song's lyrics up under.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product remembers the search name, drops the song's chosen source and asks the enabled sources again.
  kind: product
  entities:
  - entity: lyrics
    effect: changes
    facts:
    - Search name
    - Source
    - Text
    - Timing
  - entity: song
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt#searchAgainAs
---

# Search lyrics with another title

## Trigger

A song's lyrics are listed under a different name.

## Outcome

Prism looks the lyrics up again under the new title and artist, and remembers them for this song.

## Edge cases

- A blank title, or the song's own, goes back to searching under the song's own name.
