# SKV89's Smart Cut & Join v1.0.0

The first public release of a portable Windows video cutter, splitter and joiner.

## Highlights

- **Smart cut:** copy video between safe keyframes and encode the boundaries that need it, with supported CPU and NVIDIA paths.
- **Flexible editing:** keep clips or delete gaps; use automatic chronological order or explicitly allow custom order and overlaps. Export separate clips or merge them.
- **Precise navigation:** drag the playhead to scan the preview, step by frame or keyframe, and use waveform and timeline zoom controls.
- **Track control:** select and reorder audio and subtitles independently of preview choices. Supported subtitle paths include text, ASS/SSA, DVD/VobSub and PGS.
- **Join:** stream-copy compatible files or explicitly choose supported software/NVIDIA encoding, with track mapping, aspect-ratio controls and Undo/Redo.
- **Batch queue:** retain each job's cuts, tracks, output name and settings. Review elapsed time per job, retry unfinished work and clear completed entries. Saving the queue between sessions is optional and off initially.
- **Clear output checks:** Light checks packets and timing; Intermediate also decodes boundary regions; Full decodes each final output and checks its audio. Qualified NVIDIA video verification is available with CPU fallback for unsupported configurations.
- **Saved preferences:** General settings hold Cut defaults. Export-dialog overrides apply to that job. Software H.264/HEVC offer separate Balanced and Quality effort choices.
- **Local Optimization:** finish scenarios individually, repeat competitive measurements as needed, and save qualified resource recommendations automatically. Quick, Extended and Performance search have ceilings of 10, 30 and 60 active minutes per scenario.

## Download and run

Download **SKV89-Smart-Cut-Join-v1.0.0-Windows-x64.zip**, extract the entire archive, and run **SKV89's Smart Cut & Join.exe**. Keep the runtime and license folders beside it. Python is not required. On first use, choose **Settings > General > Install/update FFmpeg > Install FFmpeg** to obtain the latest stable Full build directly from Gyan.dev. This checksum-verified download requires internet access; subsequent editing and exports work offline. Existing compatible FFmpeg/FFprobe 9.0+ tools can also be used. **SHA256SUMS.txt** identifies the exact downloads.

The optional **SKV89-Smart-Cut-Join-v1.0.0-Library-Support.zip** contains instructions, a generic library-replacement utility and the PyAV loader patch. It is for exercising third-party library modification rights, and is not needed to run the app. It contains no Smart Cut & Join application source.

## Before exporting

Copied video is unchanged; encoded edges are not lossless. Compatibility depends on the input codec, track format and output container. HDR/Dolby Vision, interlaced boundary encoding and certain subtitle/audio formats remain unsupported. NVIDIA verification is currently restricted to its qualified GPU/driver and format combinations; other configurations use CPU.

The application source is private. Third-party components retain their own licenses. See **README.md**, the included **README.txt**, and **THIRD_PARTY.md** for requirements and limitations.
