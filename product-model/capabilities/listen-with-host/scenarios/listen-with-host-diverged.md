---
kind: edge
routes:
  main: Main path
steps:
- text: The guest pauses or plays something else on their own phone.
  kind: condition
  entities:
  - entity: playback
    effect: reads
    facts: []
  unattended: true
  contexts:
    main:
      place: phone::listen-together
- text: The Product marks the phone out of step and stops following the host.
  kind: product
  entities:
  - entity: together-session
    effect: changes
    facts:
    - In step
  - entity: playback
    effect: reads
    facts: []
  contexts:
    main:
      place: phone::listen-together
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt#setListenHere
---

# The guest goes out of step

## Trigger

The guest pauses or plays something else on their own phone.

## Outcome

The phone stops following the host and shows Out of step until the guest catches up.
