---
appliesTo:
- type: entity
  id: podcast-show
  effect: changes
  facts:
  - Saved
  contexts:
  - place: phone::podcast
references:
- kind: code
  role: implementation
  target: app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
permits:
- actors:
  - listener
  when:
  - entity: account
    fact: Signed in
    is: true
---

# Only a signed-in listener saves or removes podcast shows in the library

Saving and removing go to the YouTube Music account; the library changes once YouTube Music accepts them.
