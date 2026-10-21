---
id: prism
summary: An Android music client with lyrics, offline music, Replay and local-network shared listening.
category: music
tags:
- music
- android
- lyrics
- offline
authors:
- name: Yigder
license: GPL-3.0-or-later
languages:
- en
limitations:
- Catalog, streaming and account operations depend on external YouTube Music responses; Prism does not provide the
  music service.
- Listen together operates between phones on a local network and has no internet relay.
- Replay records listening on this device; podcast progress is kept separately.
- Lyric text, timing and translations depend on available provider results.
- Music files already on the phone are played where they are; Prism does not add them to YouTube Music.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: intent
  target: CONTRIBUTING.md
---

# Prism

Prism is an unofficial YouTube Music client for Android. It brings catalog discovery, music and podcast playback, lyrics, a personal library, offline music and Replay together on the phone, with Android media controls and local-network Listen together.

## Intent

In the project's words, Prism is "a YouTube Music client for Android, with word-by-word lyrics, Replay, offline downloads and full Android Auto support." It is free, has no ads and no server of its own: it talks to YouTube Music and the lyric services directly from the phone, and Listen together only talks to the other phones in the session. Signing in is optional and brings the listener's YouTube Music library, likes and playlists into the app; Replay is "a private, on-device recap of your listening".
