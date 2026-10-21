---
scope: Android music and podcast listening, discovery, personal library, offline media, lyrics, Replay, account
  connection and local-network sessions.
method: Static tracing from documented user flows through UI actions, playback, persistence and external request
  boundaries.
covered:
- description: Android entry and navigation code.
  paths:
  - app/src/main/java/com/prism/music/MainActivity.kt
  - app/src/main/java/com/prism/music/ui/Nav.kt
  - app/src/main/AndroidManifest.xml
- description: Playback, queue, media browsing, voice and car lyric code.
  paths:
  - app/src/main/java/com/prism/music/playback/PlayerConnection.kt
  - app/src/main/java/com/prism/music/playback/PlaybackService.kt
  - app/src/main/java/com/prism/music/playback/QueueState.kt
  - app/src/main/java/com/prism/music/playback/HistoryShuffleOrder.kt
  - app/src/main/java/com/prism/music/playback/MediaTree.kt
  - app/src/main/java/com/prism/music/playback/VoicePlayActivity.kt
  - app/src/main/java/com/prism/music/playback/CarLyrics.kt
  - app/src/main/java/com/prism/music/ui/player/
- description: Library, device history, collection copies and playlist state code.
  paths:
  - app/src/main/java/com/prism/music/data/LibraryRepository.kt
  - app/src/main/java/com/prism/music/data/db/
  - app/src/main/java/com/prism/music/data/OfflineLibrary.kt
  - app/src/main/java/com/prism/music/data/LikedPlaylist.kt
  - app/src/main/java/com/prism/music/data/PlaylistCovers.kt
  - app/src/main/java/com/prism/music/data/EpisodeProgress.kt
  - app/src/main/java/com/prism/music/data/model/
- description: Offline audio and video requests, predictive retention and original-file discovery code.
  paths:
  - app/src/main/java/com/prism/music/download/Downloads.kt
  - app/src/main/java/com/prism/music/download/SmartDownloads.kt
  - app/src/main/java/com/prism/music/data/local/LocalMusic.kt
  - app/src/main/java/com/prism/music/data/local/LocalLossless.kt
  - app/src/main/java/com/prism/music/AppContainer.kt
- description: Lyric selection, cache fallback, translation and file-tag request code; provider parsers supply evidence
    rather than independent guarantees.
  paths:
  - app/src/main/java/com/prism/music/data/lyrics/
  - app/src/main/java/com/prism/music/data/local/LyricsToFiles.kt
  - app/src/main/java/com/prism/music/ui/components/LyricsToFilesHost.kt
- description: Principal discovery, library, podcast and settings view code, excluding social presence, backup and updater
    branches.
  paths:
  - app/src/main/java/com/prism/music/ui/screens/HomeScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/SearchScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/ArtistScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/CollectionScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/LibraryScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/PodcastsScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/LocalMusicScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/ReplayScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/ReplayStory.kt
  - app/src/main/java/com/prism/music/ui/screens/LoginScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/SettingsScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/CatalogueScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/EqualizerScreen.kt
  - app/src/main/java/com/prism/music/data/prefs/Settings.kt
- description: Listen together session actions and local-network protocol code.
  paths:
  - app/src/main/java/com/prism/music/playback/together/
  - app/src/main/java/com/prism/music/ui/screens/TogetherScreen.kt
- description: Music sharing, account playlist selection and external transfer hand-off code.
  paths:
  - app/src/main/java/com/prism/music/data/ShareLinks.kt
  - app/src/main/java/com/prism/music/ui/components/ShareSheet.kt
  - app/src/main/java/com/prism/music/ui/components/Components.kt
  - app/src/main/java/com/prism/music/ui/screens/ImportScreen.kt
  - app/src/main/java/com/prism/music/ui/screens/LikedPlaylistSheet.kt
exclusions:
- description: Gradle and release infrastructure; build and distribution machinery rather than listening behavior.
  paths:
  - gradle/
  - build.gradle.kts
  - settings.gradle.kts
  - .github/
- description: Decorative theme, background rendering and promotional media; visual design rather than acceptance
    behavior.
  paths:
  - app/src/main/java/com/prism/music/ui/theme/
  - docs/screenshots/
  - promo/
- description: Test sources; inspected selectively as evidence but never executed or modeled as a product surface.
  paths:
  - app/src/test/
unmapped:
- description: Backup export, restore and migration UI; peripheral data portability workflow deferred.
  paths:
  - app/src/main/java/com/prism/music/data/Backup.kt
  - app/src/main/java/com/prism/music/ui/screens/BackupUi.kt
- description: Update checking and installation UI; peripheral release administration deferred.
  paths:
  - app/src/main/java/com/prism/music/data/Updates.kt
- description: Social presence sign-in and status UI; optional integration deferred.
  paths:
  - app/src/main/java/com/prism/music/playback/DiscordPresence.kt
- description: Home-screen widget-specific operations; media-session behavior covered but launcher widget contracts
    deferred.
  paths:
  - app/src/main/java/com/prism/music/widget/
- description: Detailed lossless catalog matching and rescanning; local playback and download removal covered, matching
    heuristics deferred.
  paths:
  - app/src/main/java/com/prism/music/download/LosslessSync.kt
- description: Provider-specific catalog ranking, parser and stream fallback details; external request outcomes
    covered without claiming provider semantics.
  paths:
  - app/src/main/java/com/prism/music/data/innertube/
  - app/src/main/java/com/prism/music/data/stream/
- description: Automatic artwork and canvas discovery heuristics; retained covers covered without a separate provider
    matching model.
  paths:
  - app/src/main/java/com/prism/music/data/canvas/
  - app/src/main/java/com/prism/music/data/meta/
- description: Signal-processing and beat-analysis heuristics; user settings and transition eligibility covered
    without numerical audio guarantees.
  paths:
  - app/src/main/java/com/prism/music/playback/Mix.kt
  - app/src/main/java/com/prism/music/playback/MixTempo.kt
  - app/src/main/java/com/prism/music/playback/SpatialAudioProcessor.kt
  - app/src/main/java/com/prism/music/playback/NormalizerProcessor.kt
- description: About and license presentation; peripheral informational views deferred.
  paths:
  - app/src/main/java/com/prism/music/ui/screens/LicensesPage.kt
- description: Background and artist-signature customization details; decorative variants deferred while general
    preference persistence is covered.
  paths:
  - app/src/main/java/com/prism/music/ui/screens/BackgroundsScreen.kt
  - app/src/main/java/com/prism/music/data/ArtistPrefs.kt
limitations: []
---

# Coverage
