# SKV89's Smart Cut & Join v1.0.2

## What’s new

- **Check for updates from the title bar.** Click **Check for updates** to compare your installed version with the latest stable GitHub release. When an update is available, **View release** opens its download page in your browser.
- **Copy exact keyframe cuts without starting the edge encoder.** Smart cut automatically copies the video when every retained picture can be copied safely. Delete mode now offers **Keyframe copy** when it can preserve the exact remaining footage. The export review explains which boundary needs encoding when an exact copy is unavailable.
- **Switch between Time and Frames on more files.** Ordered frame indexes remain usable when pictures share a timestamp. The frame display identifies the group so you can see which boundaries are available.
- **See what Optimization measured.** **Create output** groups the encoding settings, and **Check output** groups the decoder settings. In Results, **Export speed** times the complete export with its selected checks. **Video check speed** compares checking already-created video. Compatible saved checker settings carry through to Cut, Join and queued exports.
- **Continue unattended benchmarks.** A recoverable failure in one scenario can advance to the next. GPU work retries missing temperature readings and can be deferred while eligible CPU work continues. A measured GPU temperature of 91 °C stops the run. Lossless FFV1 tests size their clips using measured temporary storage. Results and the reason for a stop are saved.
- **Keep the runtime in the portable folder.** The main EXE loads its libraries from an app-local support folder on every launch. Keep the release ZIP for offline recovery with `tools/Repair.exe`.

## Download and upgrade

**Upgrading from public v1.0.0 or v1.0.1 requires the entire Windows x64 ZIP.** Close the old app and extract **SKV89-Smart-Cut-Join-v1.0.2-Windows-x64.zip** into a new writable folder. Copy your old `data` folder into the new app folder to keep settings, projects, export history and Optimization results. If the old app has a `runtime/ffmpeg` folder with your tools, copy it to the same location. If FFmpeg and FFprobe were beside the old EXE, put both tools and any DLLs from their build into the new `runtime/ffmpeg` folder. A compatible installation on the system PATH carries over automatically. Run **SKV89's Smart Cut & Join.exe** from the new folder.

For a new installation, extract the same complete ZIP. The app can use a compatible FFmpeg and FFprobe 9.0+ pair in `runtime/ffmpeg`, beside the EXE or on the system PATH. **Settings > General > Install/update FFmpeg** downloads Gyan’s stable Full build when needed.

The **Library Support ZIP** is optional and intended for people replacing separately licensed libraries. **SHA256SUMS.txt** provides checksums for both ZIP files.
