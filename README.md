# MUNIComb CoverFlow — Jellyfin plugin

Browse your Jellyfin music albums in a 3D coverflow, from Jellyfin's own main menu.
Tap a tile to flip it and see the tracks; tap a track to play it through
Jellyfin's existing player. UI only — no custom player, no separate auth,
LAN only.

## Version

**0.2.0.0** — built against the Jellyfin 10.9 API floor (`net8.0`,
`targetAbi` 10.9.0.0), so one build loads on Jellyfin 10.9 through 12.x.

## What's in this build

Build `6a4e3226` (2026-11-21) — the build live on MUNI, with everything
since the 0.1.0.0 build `fdfda404` (PRs #13–#22):

- **Visualizer** — five views (Flow, Particles, Wave, Geometry, Deep Space).
  Burning stars, a morphing hexagon skin, and a Deep Space view: a NASA
  deep-space image as the background with a glowing sun (the Geometry view)
  that starts small and far away and grows as the album plays. The whole
  picture slowly runs in an ellipse so a bright still image never burns
  into the TV, and the sun gradually warms toward yellow-orange.
- **Search** — the magnifying-glass button finds albums, artists, and tracks.
- **Details pane + track menu** — tap an album for a Jellyfin-style pane
  (backdrop, big art, Overview, Tags/Studio/Genre) with a 12-item track menu.
- **Queue panel** — album thumbnails, live EQ bars, invisible scroll, usage
  hints, and a "Save as playlist" button that saves the ordered queue as a
  real Jellyfin playlist. Double-click a track to play it right away;
  the queue keeps its own art per row.
- **Queue fixes** — Clear + reload now stops the old track, shuffle never
  disturbs the queue you built, and a re-queue failure is said out loud
  instead of swallowed silently.
- **Lockfile fix** — `npm ci` works (the build is reproducible from a clean
  checkout).

## Download

- **Zip (easiest):** `MUNICombCoverFlow_0.2.0.0.zip` — the DLL + `meta.json`
  in one file. Download it, unzip it, and install the two files inside.
- **Individual files:** `Jellyfin.Plugin.CoverFlow.dll` and `meta.json` —
  download them one at a time if you prefer.

## Install (Windows)

1. Find your Jellyfin plugins folder. Open File Explorer and paste one of
   these into the address bar — whichever one exists on your machine:
   - `%ProgramData%\Jellyfin\Server\plugins` (service / tray install)
   - `%LocalAppData%\jellyfin\plugins` (direct / user install)
2. Inside the plugins folder, make a folder called `MUNICombCoverFlow`,
   then inside that a folder called `0.2.0.0`.
3. Put `Jellyfin.Plugin.CoverFlow.dll` and `meta.json` into
   `plugins\MUNICombCoverFlow\0.2.0.0\`.
4. Restart Jellyfin (tray icon > Restart, or Dashboard > Restart).
5. Confirm: Dashboard > Plugins > My Plugins — MUNIComb CoverFlow
   should show as Active, version 0.2.0.0.
6. Open the plugin page from the Dashboard, flip through your albums,
   open one, and play a track.

## Install (Linux)

Same files, same layout: `<jellyfin data dir>/plugins/MUNICombCoverFlow/0.2.0.0/`
(typically `/var/lib/jellyfin/plugins/MUNICombCoverFlow/0.2.0.0/`),
then `sudo systemctl restart jellyfin.service`.

## Notes

- The plugin is a prototype at 0.2.0.0. It reads your existing music
  library and cover art; it does not change your library, your cover art,
  or Jellyfin's player.
- If the plugin does not show up after a restart, it is in the wrong
  folder, or your Jellyfin is older than 10.9.
- Upgrading from 0.1.0.0: install the new files into a fresh `0.2.0.0`
  folder and remove the old `0.1.0.0` folder, then restart Jellyfin.
