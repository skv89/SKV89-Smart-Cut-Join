# SKV89's Smart Cut & Join v1.0.3

## What’s new

- **More reliable Optimization runs.** Fixed legacy-format test generation, NVIDIA HEVC video-check comparisons, time allowances for longer trials, and progress reporting during slow Join encoding. FFV1 tests now account for all temporary outputs and retry with shorter clips when necessary. Recoverable row failures show a concise reason and allow the batch to continue.
- **Keep recommendations after driver updates.** Updating an NVIDIA driver alone no longer marks saved Optimization results for retesting or discards compatible automatic video-check settings.
- **Start with 16 encoding CPU threads.** New and factory-default settings use up to 16 threads, capped by the CPUs available to the app. Existing manual settings and measured recommendations are preserved. Output checking keeps its separate thread budget.
- **Scroll settings without changing them accidentally.** The mouse wheel over closed dropdowns and numeric fields scrolls the page. Ctrl+Z and Ctrl+Y undo and redo manual Optimization edits while protecting automatic recommendations and saved results.
- **Pause or resume by clicking the preview.** A click on the video now toggles playback.
- **Find Optimization controls beside the checkboxes.** Select all, Clear selection, Optimize selected, Stop and Resume are grouped at the upper left.
- **More reliable production exports.** Fixed legacy-codec container handling and NVIDIA HEVC checking used by real exports as well as Optimization. Joining compatible HEVC clips with copied video and AAC audio now preserves picture order and timing at the affected clip boundaries without re-encoding the video.

## Download and upgrade

**Updating from v1.0.2 or earlier requires the entire Windows x64 ZIP, not just the EXE.** Close the old app and extract **SKV89-Smart-Cut-Join-v1.0.3-Windows-x64.zip** into a new writable folder. Copy your existing `data` folder into the new app folder to retain settings, projects, export history and Optimization results. Keep the new package’s support files and `runtime/nvdec` helper.

If your old app has a `runtime/ffmpeg` folder, copy it to the same location in the new folder. If FFmpeg and FFprobe were beside the old EXE, move the pair and any DLLs supplied with that build into the new `runtime/ffmpeg` folder. A compatible pair on the system PATH is detected automatically. Run **SKV89's Smart Cut & Join.exe**.

For a new installation, extract the same complete ZIP. Python is not required. **Settings > General > Install/update FFmpeg** downloads Gyan’s stable Full build when needed; compatible FFmpeg and FFprobe 9.0+ tools can also be reused.

The **Library Support ZIP** is optional and intended for people replacing separately licensed libraries. **SHA256SUMS.txt** provides checksums for both ZIP files.
