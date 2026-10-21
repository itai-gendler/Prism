---
kind: primary
routes:
  main: Main path
steps:
- text: The listener opens Replay and picks a period.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::replay
- text: The Product works out minutes and rankings from this phone's listening, lists up to 100 songs and keeps the top 250
    for Play and Shuffle.
  kind: product
  entities:
  - entity: listening-history
    effect: reads
    facts:
    - Music
    - When
    - Time heard
    - Recent music
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
      place: phone::replay
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/ReplayScreen.kt
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/db/Database.kt
---

# Browse Replay

## Trigger

The listener opens Replay and picks a period.

## Outcome

Minutes, top songs, artists and genres for that period are shown; the top 100 songs are listed and Play or Shuffle use the top 250.

## Edge cases

- With nothing listened to yet, Replay explains that songs played for 10 seconds or more count toward it.
- Genres fill in over later visits as Prism learns them.
