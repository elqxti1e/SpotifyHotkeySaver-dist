# Spotify Hotkey Saver - Release Package

Spotify Hotkey Saver is a Windows tray app for saving the currently playing Spotify track to a playlist with global hotkeys. It includes a compact overlay with album art, playback controls, progress, and customizable colors.

This repository contains the public release package only.

## Download

Download the latest release from:

```text
https://github.com/elqxti1e/SpotifyHotkeySaver-dist/releases
```

Release assets:

- `SpotifyHotkeySaver-dist.zip`
- `SHA256SUMS.txt`

Extract the zip and run:

```text
dist/SpotifyHotkeySaver.exe
```

Keep the `dist/Assets/` folder next to the executable. The app uses bundled fonts and assets from that folder.

## Setup

Each user should create their own Spotify Developer app and enter their own Client ID in Settings. Client Secret is not used.

1. Run `SpotifyHotkeySaver.exe`.
2. Open Settings from the tray icon if it does not open automatically.
3. Click `Open Dashboard`.
4. Create a Spotify app in the Spotify Developer Dashboard.
5. Click `Copy Redirect URI` in Settings.
6. Add the copied Redirect URI to the Spotify app settings.
7. Copy the Spotify app's Client ID.
8. Paste the Client ID into `Spotify Client ID`.
9. Paste the target playlist URL or playlist ID into `Playlist ID or URL`.
10. Click `Save & Login`.
11. Approve the Spotify authorization in the browser.

Default Redirect URI:

```text
http://127.0.0.1:43879/callback
```

Use `127.0.0.1`, not `localhost`.

## Notes

- The release executable is self-contained. You do not need to install the .NET Runtime.
- Windows SmartScreen may warn on first launch because this is an unsigned personal project.
- Spotify playback controls may require Spotify Premium and an active playback device.
- If a Spotify Developer app is in Development Mode, Spotify may restrict which accounts can use it. For normal use, each user should create and configure their own Spotify Developer app.
- This repository does not include source code.

## Security

This release zip does not include any personal Spotify Client ID, Playlist ID, OAuth token, `config.json`, or `tokens.dat`.

User-specific settings and tokens are created locally at runtime:

```text
%AppData%\SpotifyHotkeySaver\config.json
%AppData%\SpotifyHotkeySaver\tokens.dat
```

OAuth tokens are encrypted with Windows DPAPI before being saved.

Logs are stored at:

```text
%LocalAppData%\SpotifyHotkeySaver\logs\
```
