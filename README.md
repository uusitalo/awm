# Automatic Airsoft Video Machine

Turns airsoft helmet-cam footage into finished videos: your **heart rate, GPS map, speed, shots and hits** drawn on the picture as a HUD,
plus title cards, game stats, highlight reels - and a built-in multitrack video editor, so the whole video can be finished in the app
(DaVinci Resolve hand-over is still there if you prefer it).

Made for my own airsoft videos (Finnish games, [kuulaportti.fi](https://kuulaportti.fi) events) and shared with friends. It runs on
**macOS, Linux and Windows**, and can spread the rendering over several computers.

> This repository is the **update channel** of the app. The app downloads new versions from the *Releases* page by itself.
> The first install comes as a package from me (see "Getting it" below).

## What it does

- **HUD overlays on your footage** - heart rate with zones and graph, GPS map and compass, speed, distance, altitude, clock and weather.
  Dozens of looks (glass, neon, retro shooter bar, comic, camo, racing telemetry ...) with live previews and hover-to-preview.
- **Data sources** - Apple Health exports (heart rate), GPX routes, the video's own clock; everything is synced by time.
- **Shots and hits** - finds shots from the audio, learns from your corrections, shows a shot / hit counter and flashes the screen on a hit.
- **Teams** - pick red, yellow or blue and a coloured band with the team name is drawn on the video.
- **Game cards and reels** - title cards, stats cards (shots, hits, distance, heart rate), recap, awards, aerial maps, highlight reels, split screen.
- **Timeline, day board and media library** - all clips of a day as pictures, trim, tag players, sort by game.
- **Multitrack video editor** - cut, trim, move and speed-change clips on a timeline with picture strips and sound curves, sound on audio tracks of
  their own (linked to their picture), titles, transitions, effects, colour LUTs (DJI Action D-Log M / HLG LUTs come with the app) and narration
  recording. A **Tags track** shows every shot, hit, game call, game mode and map view of the clips and lets you add, drag and remove them;
  adding a **Map** tag renders the map and puts it on the timeline at once. The preview plays picture, sound and playhead in step.
- **Export** - one page with presets for a file, YouTube, Instagram / TikTok vertical and Instagram feed (fit or fill the frame), with size,
  quality, colour and graphics-card choices.
- **DaVinci Resolve** - exports the overlay as a transparent video or a live Fusion plugin, and installs the helper scripts.
- **Render together** - Mac, Linux PC, Windows PC and a Docker worker (Unraid) can share the same video folder and split the render jobs.
- **Graphics-card encoding** - VideoToolbox on a Mac, VAAPI on Linux (AMD), NVENC / AMF / QuickSync on Windows.
- **Updates** - checks this repository when it starts and offers the new version.

## Getting it

| System | Package | Needs |
|---|---|---|
| macOS | app bundle (from me) | ffmpeg (Homebrew) |
| Linux | `AutomaticAirsoftVideoMachine-linux-<version>.tar.gz`, run `install.sh` | Python 3.10+, ffmpeg |
| Windows 10 / 11 | `AutomaticAirsoftVideoMachine-windows-<version>.zip`, double-click `install.bat` | internet once (it sets up Python and ffmpeg) |
| Unraid / Docker | `avm-worker-<version>-docker.tar.gz` | a render worker that follows the shared folder |

The install packages are not stored here - ask me for the current one. After the first install the app keeps itself up to date from this
repository (Settings > Updates, *Check for updates now*).

## How updates work

Every release here holds two files: `latest.json` (version, date, checksum, what is new) and `avm-app-<version>.tar.gz` (the app's own
files). The app compares the version number with its own, shows what is new, backs up the files it replaces and installs the new version.
No account or token is needed to update from this public repository. All computers should run the same version.

The full history of changes is in [CHANGELOG.md](CHANGELOG.md) inside each release archive and shown in the app under Help > What's new.

## Notes

- Python + PySide6 (Qt), Pillow, numpy, ffmpeg. Optional: onnxruntime and faster-whisper for speech and person recognition.
- Made by one person for a hobby, so expect rough edges. Bug reports are welcome as issues, with the app version number (shown in the window title).
- No license has been chosen yet: all rights reserved for now. Ask before reusing the code.
