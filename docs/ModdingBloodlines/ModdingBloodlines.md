---
layout: default
title: Modding Bloodlines
nav_order: 5
has_children: true
has_toc: false
---

# {{ page.title }}
{: .text-center }

Information on modding Vampire: The Masquerade - Bloodlines is scattered across community websites, forums, and tutorials. This page collects resources for finding mods, creating custom content, editing maps and models, scripting, and building Wabbajack modlists.

Bloodlines uses a modified version of Valve's Source Engine. General Source tutorials can be useful, but Bloodlines-specific tools and instructions should take priority where available.

## Guides

- [Extracting Mod Installers](/ModdingBloodlines/ExtractingInstallers.html)
- [Making Animated Textures](/ModdingBloodlines/AnimatedTextures.html)
- [Editing the Main Menu](/ModdingBloodlines/EditingMainMenu.html)
- [Console Commands](/ModdingBloodlines/Console%20Commands.html)
- [Create Your Own List](/Fashionista/CreateYourOwnList.html)

## Find and use mods

- [Browse Bloodlines mods on Nexus Mods](https://www.nexusmods.com/games/vampirebloodlines) for game mods and their download pages.
- [Browse Bloodlines mods on ModDB](https://www.moddb.com/games/vampire-the-masquerade-bloodlines) to find mods, add-ons, tools, and tutorials.
- [Planet Vampire's Bloodlines modding forum](https://planetvampire.freeforums.net/board/7/vtm-bloodlines-modding) for community discussions, technical information, and modding assistance.

If you use the Fashionista modlist, see its [Optional Mods](/Fashionista/OptionalMods.html) and [Fashion](/Fashionista/Fashion.html) pages for options included with that list. Check the profile-specific notes before enabling an option.

---

## Modding tools and SDK

### Bloodlines SDK

[Download the Bloodlines SDK](https://www.moddb.com/mods/vtmb-unofficial-patch/downloads/bloodlines-sdk)

The Bloodlines SDK contains tools for modifying game assets, creating maps, editing existing content, and working with Bloodlines-specific file formats.

Depending on the SDK version, available tools include:

- Hammer Editor for map creation and editing.
- Map compilation and decompilation utilities.
- Model editing and conversion tools.
- Texture conversion utilities.
- BSP entity editing tools.

### Valve Developer Community

- [Bloodlines Engine Reference](https://developer.valvesoftware.com/wiki/Vampire:_The_Masquerade_%E2%80%93_Bloodlines) - Bloodlines-specific engine information.
- [Source Engine](https://developer.valvesoftware.com/wiki/Source) - General Source Engine documentation.
- [Valve Developer Community](https://developer.valvesoftware.com/wiki/Main_Page) - Documentation covering models, materials, entities, mapping, and scripting.

**Note:** Bloodlines uses an early, modified version of Source. Modern Source tools and compilation instructions may not be directly compatible.

---

## Video tutorials

### Bloodlines-specific tutorials

- [An Old Grumpy Gangrel's tutorial playlists](https://www.youtube.com/@an_old_grumpy_gangrel/playlists) collect Bloodlines video guides.
- [Additional Bloodlines video tutorial](https://www.youtube.com/watch?v=kS_fHfvSe6o).
- [Bloodlines ModDB tutorials](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials) include guides for the SDK, Hammer, map creation, models, and other modding topics.

### General Source Engine tutorials

- [TopHATTwaffle](https://www.youtube.com/@TopHATTwaffle) - Hammer Editor tutorials covering level design, lighting, optimization, and Source mapping techniques.

General Source tutorials can help with Hammer fundamentals, although some techniques require adjustments for Bloodlines.

---

## Creating and editing maps

Bloodlines maps use the Source Engine's BSP format. Creating new interiors or modifying existing locations generally involves Hammer Editor and the Bloodlines SDK.

### Bloodlines Hammer tutorials

Wallit's *Basics of Bloodlines Modding* tutorial series covers SDK setup and map creation.

- [Part 1 - Introduction](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/basics-of-bloodlines-moding) - Installing the SDK, creating a mod, and testing it in-game.
- [Part 2 - Hammer Editor](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/basics-of-bloodlines-modding-part-2-hammer-1) - Hammer configuration, navigation, textures, and basic map editing.
- [Part 3 - Primitives and func_detail](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/basics-of-bloodlines-modding-part-3-primitive-and-func-detail) - Map geometry, primitives, and optimization.

### Hammer Editor references

- [Valve Hammer Editor](https://developer.valvesoftware.com/wiki/Valve_Hammer_Editor) - Editor documentation.
- [Your First Map](https://developer.valvesoftware.com/wiki/Your_First_Map) - Basic Source mapping workflow.
- [Brush Geometry](https://developer.valvesoftware.com/wiki/Brush) - Creating rooms, walls, floors, and other geometry.
- [Entities](https://developer.valvesoftware.com/wiki/Entity) - Interactive objects, triggers, NPCs, and map entities.
- [Lighting](https://developer.valvesoftware.com/wiki/Lighting) - Interior lighting and lighting configuration.
- [Level Transitions](https://developer.valvesoftware.com/wiki/Level_Transitions) - Connecting maps and managing transitions.

### Editing existing maps

Existing BSP maps can be inspected and modified using tools supplied with the Bloodlines SDK.

Changes to map geometry generally require editing and recompiling the map.

For entity-only modifications, the Bloodlines Script Extender (BLSE) provides map patches that can add, modify, or remove entities without replacing the original BSP.

See the BLSE section below for more information.

---

## Character models and textures

Creating or modifying Bloodlines character models requires working with the game's model formats, textures, materials, skeletons, and animations.

### Bloodlines-specific model tools

These tools support Bloodlines' modified Source model format (MDL v2531) and are preferable to standard Source utilities when working with Bloodlines character models.

- [Crowbar-VTMB](https://github.com/robsonner/Crowbar-VTMB/releases/tag/v0.74-vtmb.3) - Bloodlines-specific fork of Crowbar for decompiling models, including meshes, skeletons, animations, and physics data.
- [StudioMDL-VTMB](https://github.com/robsonner/studiomdl-vtmb/releases/tag/studiomdl-vtmb_0.2.1_win32) - Native Bloodlines model compiler supporting custom and modified character models, including facial animations.
- [Planet Vampire - Crowbar and Native Compiler](https://planetvampire.freeforums.net/thread/303/modding-crowbar-support-native-compiler) - Community discussion covering these tools and their development.

### Basic model workflow

1. Decompile an existing Bloodlines model using Crowbar-VTMB.
2. Import and modify the model in Blender using compatible Source model tools.
3. Export the edited model and update its QC compilation script.
4. Compile the model using StudioMDL-VTMB.
5. Install the resulting model and textures in Bloodlines for testing.

### Bloodlines model tutorials

- [Bloodlines Model Editing Lessons](https://planetvampire.freeforums.net/thread/64/vtmb-bloodlines-model-editing-lessons) - Community model editing tutorials.
- [Compiling a Custom PC Model](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/compiling-a-custom-pc-model-with-ddlullus-mdl-formatter) - Compiling custom player character models using DDLullu's MDL Formatter.

### General model creation references

- [Valve Model Creation Overview](https://developer.valvesoftware.com/wiki/Model_Creation_Overview) - General Source model development.
- [Blender Source Tools](https://developer.valvesoftware.com/wiki/Blender_Source_Tools) - Exporting models and animations from Blender.
- [QC File Documentation](https://developer.valvesoftware.com/wiki/QC) - Model compilation scripts.
- [StudioMDL](https://developer.valvesoftware.com/wiki/StudioMDL) - Standard Source model compilation documentation.

**Important:** Standard Source model compilation tools do not necessarily produce models compatible with Bloodlines. Use the Bloodlines-specific tools and tutorials for the required compilation process.

### Textures and materials

- [VTF Texture Format](https://developer.valvesoftware.com/wiki/VTF) - Source texture files.
- [VMT Material Format](https://developer.valvesoftware.com/wiki/VMT) - Material definitions and texture references.
- [Material Proxies](https://developer.valvesoftware.com/wiki/Material_proxies) - Dynamic material effects and animations.

Bloodlines also uses `.tth` and `.ttz` texture files. The Bloodlines SDK includes conversion tools for working with these formats.

---

## Bloodlines Script Extender (BLSE)

[Bloodlines Script Extender - Official Website and Documentation](https://bigbannng.github.io/blse-dev/index.html)

BLSE expands the scripting and modding capabilities of Vampire: The Masquerade - Bloodlines.

It supports Python scripts, native C++ plugins, custom content, and a modular system for loading game assets without directly replacing original files.

BLSE requires Bloodlines with the Unofficial Patch (Basic or Plus).

### Main documentation

- [BLSE Overview](https://bigbannng.github.io/blse-dev/index.html) - Features, requirements, and installation.
- [Documentation Index](https://bigbannng.github.io/blse-dev/docs/) - Complete reference documentation.
- [Installation and Troubleshooting](https://bigbannng.github.io/blse-dev/docs/installing.html) - Installation and diagnostics.
- [Python Modding](https://bigbannng.github.io/blse-dev/docs/python/) - Creating scripts and using the BLSE Python API.
- [Mod Folders](https://bigbannng.github.io/blse-dev/docs/python/mod-folders.html) - Packaging custom content and managing compatibility.

### Python API documentation

| Documentation                                                                             | Purpose                                    |
| :---------------------------------------------------------------------------------------- | :----------------------------------------- |
| [Events](https://bigbannng.github.io/blse-dev/docs/python/events.html)                    | Respond to game events and player actions  |
| [Dialogue](https://bigbannng.github.io/blse-dev/docs/python/dialogue.html)                | Create and modify conversations            |
| [Items and Inventories](https://bigbannng.github.io/blse-dev/docs/python/items.html)      | Custom items, inventory, and merchants     |
| [World and Entities](https://bigbannng.github.io/blse-dev/docs/python/world.html)         | Spawn and manipulate game entities         |
| [Models and Appearance](https://bigbannng.github.io/blse-dev/docs/python/appearance.html) | Character skins, materials, and appearance |
| [Animation](https://bigbannng.github.io/blse-dev/docs/python/animation.html)              | Control and modify animations              |
| [Saved Data](https://bigbannng.github.io/blse-dev/docs/python/saved-data.html)            | Persistent mod variables and settings      |
| [Screens and Windows](https://bigbannng.github.io/blse-dev/docs/python/screens.html)      | Custom interface elements and windows      |

### Mod folders and compatibility

BLSE allows mods to package their content into separate folders containing assets such as:

- Models and materials.
- Maps and map entity patches.
- Dialogue and scripts.
- Sounds and animations.
- Items, quests, and other game data.

BLSE also provides merge functionality for supported game data files, reducing the need for multiple mods to replace the same files.

Map patches can modify entities in existing maps without recompiling their geometry.

These features can simplify compatibility between independently developed mods, although conflicting modifications may still require testing.

### Native plugins

BLSE also supports native C++ plugins for functionality requiring direct interaction with the game engine.

The [official documentation](https://bigbannng.github.io/blse-dev/docs/) includes plugin development, events, hooks, interface modification, and Direct3D rendering.

---

## Changing clans

ModDB's *How to Change Clans* tutorial series covers modifying the game's existing clan system.

[Part 1](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-1) · [Part 2](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-2) · [Part 3](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-3) · [Part 4](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-4) · [Part 5](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-5) · [Part 6](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-6) · [Part 7](https://www.moddb.com/games/vampire-the-masquerade-bloodlines/tutorials/how-to-change-clans-part-7).

---

## Texture and interface modifications

### Animated textures

See [Making Animated Textures](/ModdingBloodlines/AnimatedTextures.html) for a workflow using animated VTF textures, the Bloodlines texture converter, and an `AnimatedTexture` proxy in `death.vmt`.

### Main menu

See [Editing the Main Menu](/ModdingBloodlines/EditingMainMenu.html) for information about:

- Replacing main menu logos.
- Editing particle effects.
- Changing skybox textures.
- Working with Bloodlines texture files.

---

## Build a Wabbajack modlist

The [Create Your Own List](/Fashionista/CreateYourOwnList.html) guide explains the Fashionista Wabbajack setup, including:

- Mod Organizer 2.
- Stock Game Folder.
- Root Builder.
- Unofficial Patch integration.
- Wabbajack compilation.

This is an advanced guide based on Fashionista's existing setup.

### Extracting mod installers

Some Bloodlines overhauls are distributed as executable installers rather than standard archives.

See [Extracting Mod Installers](/ModdingBloodlines/ExtractingInstallers.html) for information on extracting Inno Setup installers and examining their contents before repackaging them for Mod Organizer 2.

---

## Other reference pages on this site

- [Fashionista Modlist](/Fashionista/Modlist.html) - Mod load order and included modifications.
- [Fashionista Files](/Fashionista/Files.html) - Files and downloads used by the modlist.
- [Fashionista Optional Mods](/Fashionista/OptionalMods.html) - Optional modifications and compatibility notes.

---

*Bloodlines modding tools and documentation continue to evolve. Some older tutorials use legacy versions of the SDK or Unofficial Patch, so procedures may differ from current releases.*