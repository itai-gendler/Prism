---
singleton: true
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/playback/together/Together.kt
---

# Listen together session

The local-network session hosted by one phone and joined by other phones. Each phone loads its own audio.

## Information kept

- **Host** — Host name and local-network address.
- **Code** — The displayed joining code.
- **Guests** — Names of currently connected guests.
- **Guest control** — Whether the host permits guest playback commands.
- **Now playing** — Host music, current position, playing state and upcoming entries.
- **Play here too** — Whether a guest follows on their own phone.
- **In step** — Whether local playback is following the host or has diverged.
- **Connection** — Joining, connected or ended status and an explanatory message.

## States

### Idle

This phone has no active session.

### Hosting

This phone is hosting.

### Joining

This phone is connecting to a host.

### Joined

This phone has joined a host.
