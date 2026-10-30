# SKV89's Smart Cut & Join v1.0.1

This update improves editing of files with irregular timestamps and makes the Export dialog clearer.

## Changes

- **Keep editing when frame indexing is unreliable.** The app switches to Time mode instead of leaving Set Start and Set End disabled. Opening a healthy file restores your preferred frame display.
- **Handle repeated video timestamps more reliably.** Unaffected ranges can still use smart cut. When a selection includes distinct pictures sharing a timestamp, full-segment encoding can retain those pictures with repaired timing while keeping audio and subtitles aligned. Choose FFV1 when lossless full-segment encoding is needed.
- **Prevent stray hover help at startup.** Restoring a saved dropdown selection no longer shows a tooltip before the main window is ready.
- **Show useful export notes without interrupting work.** Amber notes are reserved for unresolved concerns. Successful automatic scan fallbacks and timestamp repairs remain in job details. No extra loading scans or queue confirmation prompts are added.
- **Tidy the Export dialog.** Dropdowns share a common left edge, descriptions use natural paragraph spacing, and Export/Cancel remain accessible when the options need scrolling.

Fast source analysis and Light output checks remain the Cut defaults. Fast still falls back to a full source scan when needed. Full output decoding remains optional.

## Download and update

- **First-time installation:** download `SKV89-Smart-Cut-Join-v1.0.1-Windows-x64.zip`, extract the **entire ZIP**, and keep its folders together.
- **Updating an existing v1.0.0 installation:** close the app, extract the ZIP elsewhere, then copy **only `SKV89's Smart Cut & Join.exe`** into the existing app folder. Keep `runtime`, `licenses` and `data`. No FFmpeg reinstallation is required. Refreshed documentation is included but optional to copy.
- **Library Support ZIP:** optional tools and instructions for replacing separately licensed libraries; not needed for normal use.
- **SHA256SUMS.txt:** checksums for both ZIP files.

Requires Windows x64. FFmpeg and FFprobe 9.0 or newer are separate tools. The app checks `runtime/ffmpeg`, its own folder and explicit absolute PATH locations. If needed, use **Settings > General > Install/update FFmpeg** to download the latest stable Full build directly from Gyan.dev.

HDR/Dolby Vision and interlaced re-encoding remain outside the supported encoding paths. Damaged files and unsupported codec/container combinations can still require conversion or repair.
