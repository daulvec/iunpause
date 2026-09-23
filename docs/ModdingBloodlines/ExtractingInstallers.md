---
layout: default
title: Extracting mod installers
parent: Modding Bloodlines
nav_order: 1
---

# {{ page.title }}

Some Bloodlines overhauls use an Inno Setup `.exe` installer with several optional components. Extracting the installer lets you inspect its files and build separate MO2 mods for the options you want, without running the installer against your game folder.

## Extract with innounp

1. Download `innounp.exe` from the [Inno Setup Unpacker site](https://innounp.sourceforge.net/).
2. Put `innounp.exe` in the same folder as the overhaul's installer `.exe`.
3. Open PowerShell in that folder.
4. Replace `OverhaulSetup.exe` with the actual installer filename and run:

   ```powershell
   .\innounp.exe -x -d"C:\extract" ".\OverhaulSetup.exe"
   ```

5. Open `C:\extract\{app}` and inspect the extracted files. Optional components may be in folders named `Xtras` or similar.
6. Build your MO2 mod or mods from the extracted content, keeping only the options you intend to use.

The `-x` option extracts files with their paths, and `-d` sets the destination directory. If innounp cannot read an installer, it may use an unsupported Inno Setup format; do not assume the `.exe` contains no mod files.
