---
kind: alternate
routes:
  main: Main path
steps:
- text: The session guest opens Listen together.
  kind: actor
  entities: []
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
- text: The Product shows the host, who is listening, what is playing and what is up next.
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
  actor: session-guest
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/TogetherScreen.kt
---

# See the session as a guest

## Trigger

A guest opens Listen together.

## Outcome

The guest sees the host, who is listening, what is playing and what is up next.
