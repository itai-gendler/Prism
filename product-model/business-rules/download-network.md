---
appliesTo:
- type: entity
  id: download
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/download/Downloads.kt#applyRequirements
---

# Downloads wait for the network they are allowed to use

With Wi-Fi only on, downloads wait for Wi-Fi. When Smart Downloads may use mobile data, its picks download on any network while they are the only downloads waiting; a song or video the listener downloaded keeps everything waiting for Wi-Fi.
