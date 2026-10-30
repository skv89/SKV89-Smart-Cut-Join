# Third-party components

SKV89's Smart Cut & Join is an independent application. Third-party components retain their own copyrights and licenses; the application license does not replace those terms.

| Component | Use | License information |
| --- | --- | --- |
| [FFmpeg and ffprobe](https://ffmpeg.org/) | Separate media-processing tools, downloaded by the user from Gyan.dev | GPLv3; linked components have additional terms. Not included in this ZIP. |
| [FFmpeg shared libraries](https://github.com/BtbN/FFmpeg-Builds) | Media reading and processing through PyAV | BtbN LGPL variant, LGPLv3 or later, without in-process x264/x265. |
| [mpv](https://mpv.io/) | Video, audio and subtitle preview | GPLv2 or later; linked components retain their own terms. |
| [Qt, PySide6 and Shiboken](https://www.qt.io/qt-for-python) | Desktop interface | Applicable libraries under LGPLv3; upstream alternatives and notices retained. |
| [PyAV](https://github.com/PyAV-Org/PyAV) | Media bindings | BSD-3-Clause; adapted to load the bundled LGPL FFmpeg libraries. |
| [smartcut](https://github.com/skeskinen/smartcut) | Smart rendering foundation | MIT, with local adaptations. |
| [NumPy](https://numpy.org/) | Numeric processing | BSD and included component licenses. |
| [Pillow](https://python-pillow.org/) | Image support | MIT-CMU and included component licenses. |
| [OpenSSL 3.5.8](https://github.com/openssl/openssl/tree/openssl-3.5.8) | Python HTTPS downloads | Apache-2.0; license and author notices in the licenses folder. |
| [Python](https://www.python.org/) | Embedded language runtime | PSF and included component terms. |
| [PyInstaller](https://pyinstaller.org/) | Application packaging | GPL with bootloader exception. |
| [Lucide](https://lucide.dev/) | Interface icons | ISC and retained attributions. |
| [NVIDIA nv-codec-headers](https://github.com/FFmpeg/nv-codec-headers) | Declarations used by the video-verification helper | Permissive NVIDIA header notice in `licenses/NVDEC_HEADERS.txt`; driver DLLs are not included. |

License texts and notices are in the portable package's `licenses` folder. The Gyan installer retains the downloaded tool's README and license in `runtime/ffmpeg`. Gyan supplies those separate downloads; this release does not mirror their executables.

Third-party source and library-replacement rights remain governed by the applicable component licenses. These rights are separate from the private application source. There is no affiliation with or endorsement by the listed projects.

Corresponding sources, dependency revisions, build scripts and patches for the distributed components are linked in [THIRD_PARTY_SOURCES.md](THIRD_PARTY_SOURCES.md). [LIBRARY_REPLACEMENT.md](LIBRARY_REPLACEMENT.md) describes the optional replacement utility. It contains no Smart Cut & Join application source.
