# Replacing separately licensed libraries

The portable v1.0.3 package loads its native libraries from the `support-*` folder beside the main EXE. The application license permits modifying or replacing LGPL libraries and reverse engineering to debug those modifications. Consult [third-party sources and build instructions](THIRD_PARTY_SOURCES.md) for the versions, patches and licenses.

## External libraries and tools

1. Extract the complete Windows ZIP into a separate writable folder. Close that copy of the app before replacing anything.
2. Place a compatible modified library at the same path in that copy. Qt and PySide6 are under `support-*/PySide6/`, Shiboken under `support-*/shiboken6/`, and PyAV’s LGPL FFmpeg DLLs under `support-*/av/_dlls/`. Preserve the library names, compatible Windows x64 interfaces and the Python 3.12 extension ABI.
3. Launch the test copy with its existing support-folder name. The main EXE loads the external libraries. `tools/Repair.exe` restores original distribution files from the release ZIP, so keep your modified libraries separately if you use Repair.

The mpv player can be replaced in `runtime/mpv/`. FFmpeg and FFprobe can be installed together in `runtime/ffmpeg/`. Their replacement is independent of the shared FFmpeg libraries used by PyAV.

## Python library modules embedded in the EXE

The optional **SKV89-Smart-Cut-Join-v1.0.3-Library-Support.zip** includes a generic replacement utility and the PyAV loader patch. You can use it to replace embedded PySide6 or Shiboken Python modules while retaining the application object code.

1. Extract the Library Support ZIP. In that folder, use Windows x64 Python 3.12 to prepare the utility:

```powershell
py -3.12 -m venv library-env
.\library-env\Scripts\python.exe -m pip install PyInstaller==6.22.3
```

2. List the replaceable modules in the **original** application EXE:

```powershell
.\library-env\Scripts\python.exe replace_libraries.py "C:\SmartCut\SKV89's Smart Cut & Join.exe" --list
```

3. Create a UTF-8 JSON file called `replacements.json` that maps an entry from the list to the corresponding modified upstream Python source file. For example:

```json
{"PYZ/PySide6": "modified/PySide6/__init__.py"}
```

4. Write a new executable. The utility checks that unrelated archive entries and modules retain their contents:

```powershell
.\library-env\Scripts\python.exe replace_libraries.py "C:\SmartCut\SKV89's Smart Cut & Join.exe" --replace replacements.json --output "C:\Modified\SKV89's Smart Cut & Join.exe"
```

The output directory must already exist, and the output filename must be new. Put the new EXE beside the matching support, runtime and other folders from your test copy. Run the affected feature there. For an inventory of the included components, see [third-party notices](THIRD_PARTY.md).
