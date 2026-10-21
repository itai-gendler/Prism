---
kind: primary
routes:
  main: Main path
steps:
- text: The listener picks another source in Lyrics source.
  kind: actor
  entities:
  - entity: lyrics
    effect: reads
    facts: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product remembers the source for this song and shows its lyrics with their timing level.
  kind: product
  entities:
  - entity: lyrics
    effect: changes
    facts:
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
  target: app/src/main/java/com/prism/music/ui/player/PlayerLyrics.kt#select
---

# Change the lyrics source

## Trigger

The listener wants this song's lyrics from another source.

## Outcome

The song shows lyrics from the chosen source from now on, with the timing that source offers.

## Edge cases

- A source with no lyrics for the song shows none while it is chosen.
