---
kind: primary
routes:
  main: Main path
steps:
- text: The session guest chooses Play next or Add to queue on a song.
  kind: actor
  entities:
  - entity: song
    effect: reads
    facts: []
  - entity: queue
    effect: reads
    facts: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product sends the song to the host, who queues it and shows who added it.
  kind: product
  entities:
  - entity: song
    effect: reads
    facts:
    - Title
    - Artists
  - entity: queue
    effect: changes
    facts:
    - Entries
    - Added by listener
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#suggest
---

# Add a song to the host's queue

## Trigger

A guest in a session wants a song played.

## Outcome

The song goes into the host's queue, next or at the end, and the host sees who added it.
