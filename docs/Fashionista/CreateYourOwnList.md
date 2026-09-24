---
layout: default
title: Create your own list
parent: Reference
nav_order: 4
has_children: false
has_toc: true
---

# {{ page.title }}
{: .text-center }

This is an advanced guide to building a Bloodlines Wabbajack list with Mod Organizer 2 (MO2). It documents the approach used while developing Fashionista. If you only want to install Fashionista, follow the [installation guide](/Fashionista/Installation.html) instead.

## Before you start

You will need a clean Bloodlines installation, a portable MO2 installation, the Bloodlines MO2 game plugin, the Unofficial Patch installer, and Wabbajack. Keep a separate working folder for extracting installers and a downloads folder for the archives your list will use. The [extracting mod installers](/ModdingBloodlines/ExtractingInstallers.html) guide covers overhauls packaged as Inno Setup `.exe` files.

Decide which store version you will build against. Fashionista publishes separate [Steam and GOG lists](/Fashionista/Changelog.html#gog-list-availability), even though they contain the same mods and profiles. Test the output against the game installation it is meant to support.

## 1. Set up MO2

1. Install MO2 as a **portable** instance so its configuration and mods stay with the list.
2. Install a Bloodlines game plugin. The basic games plugin is at `plugins\basic_games\game\game_vampirebloodlines.py` inside MO2. Its `GameDataPath` determines the default destination when installing mods. Set it to the folder your list uses, such as `Unofficial_Patch`, when the default `vampire` folder is not appropriate.
3. Create a profile and confirm that MO2 can launch your chosen game installation before adding the rest of the list.

For several overhaul profiles with different game folders, see the [custom Bloodlines MO2 plugin](https://github.com/daulvec/Bloodlines_MO2_Plugin). It can provide profile-specific mod folders for saves and INI files, along with executable selection and icon options, but it requires more manual setup.

## 2. Choose how to handle game files

| Approach | Useful when | Main tradeoff |
| --- | --- | --- |
| Stock game folder | You want an isolated copy of the game inside the list. | The copied base files tie the list to the store build used to create them. |
| Root Builder | You need MO2 mods to place files beside `vampire.exe`. | Putting many files through Root Builder can make launch slower and setup more involved. |
| Both | You need an isolated game copy and selected root-level files from MO2 mods. | You must maintain both the stock folder and Root Builder layout. |

With Root Builder, put files that must land in the game root inside a `Root` folder in the relevant MO2 mod. Keep ordinary files out of that folder. For a large mod such as the Unofficial Patch, separate root-level files from files that MO2 can load normally; this reduces the number of files Root Builder has to process.

If you copy a game installation into a stock folder, build and test it for the same store version. The [Fashionista requirements](/Fashionista/Installation/Requirements.html) describe the Steam and GOG versions supported by Fashionista; your own list needs its own compatibility testing.

## 3. Split the Unofficial Patch into MO2 mods

The Unofficial Patch installer patches `vampire.exe`, so prepare it in a temporary folder rather than installing all of its files into the game folder you are building from.

1. Copy `vampire.exe` from the store installation into a short working path, for example `C:\VTMB-work`. A short path also helps avoid Windows path-length problems.
2. Run the Unofficial Patch installer and select that working folder as its destination. Choose either **Core** or **Plus** for the list you are building. Core keeps the base-game approach; Plus includes restored content.
3. After installation, make an MO2 mod called **Unofficial Patch - Root**. Inside it, create a `Root` folder and put the files from the top level of the working folder there, excluding the `Unofficial_Patch` directory.
4. Make a second MO2 mod called **Unofficial Patch - Game Data**. Put the contents of the working folder's `Unofficial_Patch` directory in this mod, with its files at the mod's top level.
5. Enable both mods and launch the game through MO2. Check that the executable and patch content used by the selected profile work together before adding more mods.

These names distinguish the two parts of the patch in MO2. Adjust the game-data mod layout if your game plugin expects a different folder structure.

## 4. Add optional root-level components

ReShade is one example of a component that needs files in the game root. The following is a workflow example; use the setup program and files supplied with the ReShade version you choose.

1. Make a temporary folder for the ReShade option and copy `vampire.exe` into it.
2. Put the preset's `.ini` file in that folder. Run the ReShade setup program against the copied executable and select **DirectX 9** and the preset when prompted.
3. Remove the temporary executable after setup. Review the generated files, including any license or redistribution terms, before packaging them in your list.
4. Put the files that need to land beside the game executable inside a `Root` folder in their MO2 mod.
5. If you want these shortcuts, edit the generated `ReShade.ini`:

   ```ini
   [INPUT]
   ; Control + F12 toggles effects
   KeyEffects=123,1
   ; Control + F11 toggles the overlay
   KeyOverlay=122,1
   ```

Keep the license supplied with the component you actually package. Do not add a placeholder license just to affect compilation.

For an ENB option, a configuration may include shortcuts such as:

```ini
[INPUT]
KeyUseEffect=123 ; Shift + F12
KeyBloom=120
KeyOcclusion=121
```

Check shortcuts and conflicts in game for each graphics option you include.

## 5. Prepare download metadata

MO2 can create metadata for downloads made with **Download with Manager**. Some manually downloaded files need a companion `.meta` file in the list's downloads folder so Wabbajack can identify their source.

### ModDB downloads

For a ModDB download that opens a download frame, open that frame in a new tab to find the direct download page. A manual metadata file can look like this; replace the URL and prompt with values for the actual archive:

```ini
[General]
installed=true
manualURL=https://www.moddb.com/addons/start/174197
prompt=Wait for the download to start automatically for NewPCMod.1.rar
```

### Nexus Mods downloads

If **Download with Manager** is unavailable, download the archive manually and use its Nexus file page to find the mod ID and file ID. A Nexus URL containing `/mods/80?tab=files&show_file=1581` gives `modID=80` and `fileID=1581` for this **example**. These values can change with the file you download.

Create a text file beside the archive using the archive's exact name followed by `.meta`, for example `PatchInstaller.exe.meta`. Fill in the IDs for your download:

```ini
[General]
gameName=vampirebloodlines
modID=80
fileID=1581
```

The Unofficial Patch is one example of a file that may need this manual step. Check the current download page instead of copying the sample IDs without verification.

## 6. Compile and test the list

In Wabbajack's compile settings, **AlwaysEnable** can include an optional mod that is disabled in the default MO2 profile. **NoMatchInclude** can inline files that Wabbajack cannot match to an archive. Use the latter only for files you are allowed to distribute, and inspect the compiler output to confirm what was included.

Compile the list, install the resulting file into a fresh location, and launch each profile and graphics option you intend to support. Confirm that the selected Steam or GOG build, MO2 paths, Root Builder files, downloads, and metadata all work from that fresh installation.

## Further references

- [Bloodlines modding resources](/ModdingBloodlines/ModdingBloodlines.html) collects forums, model tutorials, and other game-editing references.
- [Editing the Bloodlines main menu](/ModdingBloodlines/EditingMainMenu.html) covers menu textures, particles, and skybox files.
- [MO2 wiki](https://github.com/ModOrganizer2/modorganizer/wiki) and [basic games plugins](https://github.com/ModOrganizer2/modorganizer-basic_games) provide MO2 reference material.
- [MO2 Python plugin](https://github.com/ModOrganizer2/modorganizer-plugin_python) is a starting point for plugin development.
