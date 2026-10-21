---
kind: primary
routes:
  main: Main path
steps:
- text: The listener turns Autoplay on.
  kind: actor
  entities: []
  actor: listener
  contexts:
    main:
      place: phone::player
- text: The Product turns Autoplay on and asks for similar music as the queue nears its end.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Autoplay
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Suggestions
  actor: listener
  contexts:
    main:
      place: phone::player
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/PlaybackService.kt#onAutoplayChanged
---

# Turn Autoplay on

## Trigger

The listener wants the music to keep going after the queue ends.

## Outcome

Autoplay is on and similar music is added as the queue nears its end.
