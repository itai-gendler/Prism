---
kind: primary
routes:
  main: Main path
steps:
- text: The session host chooses Start a session.
  kind: actor
  entities: []
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
- text: The Product starts the session, makes it findable on the network and shows its code.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    from: Idle
    to: Hosting
    facts:
    - Host
    - Code
    - Guests
    - Guest control
    - Connection
  actor: session-host
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#host
---

# Start a session

## Trigger

The listener wants friends on the same Wi-Fi or hotspot to listen along.

## Outcome

The session is running and shows its four-digit code and address for guests.

## Edge cases

- If the session cannot be opened on the network, Prism says so and no session runs.
