---
kind: alternate
routes:
  main: Main path
steps:
- text: The session host opens Listen together.
  kind: actor
  entities: []
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
- text: The Product shows the session code, who is listening and what is playing.
  kind: product
  entities:
  - entity: together-session
    effect: reads
    facts:
    - Host
    - Code
    - Guests
    - Guest control
    - Now playing
    - Play here too
    - In step
    - Connection
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
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/TogetherScreen.kt
---

# See the session as the host

## Trigger

The host opens Listen together.

## Outcome

The host sees the session code, who is listening and what is playing.
