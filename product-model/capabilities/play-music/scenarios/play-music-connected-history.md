---
kind: alternate
routes:
  main: Android app
steps:
- text: The listener plays a catalog song while signed in.
  kind: actor
  actor: listener
  entities:
  - entity: song
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
- text: The Product reports the play to the listener's YouTube Music history.
  kind: product
  actor: listener
  entities:
  - entity: account
    effect: reads
    facts:
    - Signed in
  - entity: song
    effect: reads
    facts:
    - Source
  - entity: listening-history
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#loadExtras
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/data/innertube/YouTubeMusic.kt#registerPlayback
---

# Signed-in plays reach YouTube Music history

## Trigger

The listener plays a catalog song while signed in.

## Outcome

The play is added to the listener's YouTube Music history, so its recommendations keep up; Replay is kept on the phone either way.
