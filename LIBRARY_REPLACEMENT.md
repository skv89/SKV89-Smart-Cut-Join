# Replacing separately licensed libraries

Third-party library licenses remain in force. The application license permits modifying or replacing LGPL libraries and reverse engineering to debug those modifications. The distributed application object code is retained when recombining a new executable; private application source is not needed for this procedure.

The optional **SKV89-Smart-Cut-Join-v1.0.0-Library-Support.zip** release asset contains a small, MIT-licensed replacement utility and the PyAV loader patch. It is not needed for ordinary app use.

## External tools

The mpv preview player is a separate executable at `runtime/mpv/mpv.exe`. An interface-compatible replacement can be placed there in a copy of the app folder. FFmpeg and FFprobe are separate user-installed tools at `runtime/ffmpeg`, beside the app EXE, or on an explicit absolute system PATH. Keep matching dependencies together. No repacking is necessary for these tools.

## Libraries packed inside the app EXE

The executable contains Qt/PySide6 under `PySide6/`, Shiboken under `shiboken6/`, and LGPL FFmpeg libraries under `av/_dlls/`. PySide6/Shiboken Python modules are also packed in `PYZ.pyz`; the utility lists these with a `PYZ/` prefix. The replacement utility lists, extracts and replaces those entries while retaining all other application object code and launch options, including every unrelated Python module. It writes a new executable and refuses to overwrite the input or an existing output.

1. Make a separate copy of the entire app folder. Keep your original application and data intact. Close the test copy before replacing its libraries.
2. Obtain modified library sources and build instructions from [THIRD_PARTY_SOURCES.md](THIRD_PARTY_SOURCES.md). Build compatible Windows x64 libraries. Keep Qt/PySide/Shiboken versions compatible, and preserve the FFmpeg library major ABIs. The packaged Python runtime is CPython 3.12 x64; Python extension bindings must remain compatible with it.
3. Extract the optional Library Support ZIP. On a Windows machine with Python 3.12, create a separate utility environment and install its archive-reading dependency:

```powershell
py -3.12 -m venv library-env
.\library-env\Scripts\python.exe -m pip install PyInstaller==6.22.3
```

4. List the replaceable entries. Optionally extract them to a new directory for inspection:

```powershell
.\library-env\Scripts\python.exe replace_libraries.py "C:\MyApp\SKV89's Smart Cut & Join.exe" --list
.\library-env\Scripts\python.exe replace_libraries.py "C:\MyApp\SKV89's Smart Cut & Join.exe" --extract "C:\LibraryWork\original-libraries"
```

The extraction destination must not exist, and its parent must exist. Only the separately licensed library entries are extracted. Packed Python library modules are extracted as `.pyc` object code under `PYZ/`; obtain their editable `.py` sources from the matching upstream source tree.

5. Create `replacements.json`, mapping the listed entry names to your modified files. Forward slashes are accepted:

```json
{
  "PySide6/Qt6Core.dll": "C:/LibraryWork/modified/Qt6Core.dll",
  "PYZ/PySide6.support": "C:/LibraryWork/modified/support/__init__.py"
}
```

Either or both kinds of replacement can be supplied. A `PYZ/` replacement must be a complete `.py` source file for that listed PySide6/Shiboken module; it is compiled with Python 3.12 without running it. Private application modules cannot be targeted. Include every related library, Python module or plugin that your change requires. Relative replacement paths resolve from the directory containing this JSON file.

6. Recombine a new executable beside the copied app's runtime and license folders:

```powershell
.\library-env\Scripts\python.exe replace_libraries.py "C:\MyApp\SKV89's Smart Cut & Join.exe" --replace replacements.json --output "C:\MyApp\SmartCut-modified.exe"
```

The utility verifies each rebuilt archive entry and checks that all other entries and the original executable remain unchanged. It supports this unsigned v1.0.0 executable; it refuses signed executables rather than silently removing a signature. Start the new executable from the copied folder and test the behavior affected by your library change. Modified libraries must retain compatible APIs/ABIs to work with existing application object code.

## PyAV loader change

The supplied `PyAV-16.0.1-local-dll-loader.patch` is the local change to PyAV's library loading. Apply it to the linked PyAV 16.0.1 source when rebuilding those bindings. It adds `av/_dlls` to the DLL search path before importing bindings. It is separately licensed PyAV code, not Smart Cut & Join application source.
