---
layout: default
title: Create your own list
parent: Reference
nav_order: 4
has_children: false
has_toc: false
---

{: .text-center }
# {{ page.title }}

Advanced guide for creating your own custom Wabbajack modlist based on Fashionista.

## Creating your own List

Here is some information I have found on modding this game using Wabbajack and ModOrganizer2, that I am organizing here in case it comes in handy for anyone else, as well as to make it easy for me to find if I need it again.

## Setting Up Mod Organizer

- Mod Organizer needs to be installed as the Portable Version.
- The plugin for the game is here: `\ModOrganizerFolder\plugins\basic_games\game\game_vampirebloodlines.py`
- The `GameDataPath = "vampire"` is the path that it defaults to for installing mods, you probably want to update it to `Unofficial_Patch`

### Stock Game Folder vs Root Builder

There are 2 main options for setting up the game for a Wabbajack list and I will try to outline the pros and cons of each method here.

#### Stock Game Folder

The Stock Game Folder method copies all the game files into a folder in Mod Organizer and then launches the game from this folder.

{: .warning}
> **Outdated** - GOG is not currently working so I would suggest using the Stock Game folder method at this time.


##### Pros

- Probably the easiest to set up
- Will let you have multiple lists installed without having issues with other lists
  - This is currently not a big deal as this is the only VtM:B list, but this could change in the future.
- You can add an ENB to the Stock Game folder
- You can install the Unofficial Patch to the Stock Game folder and this is the easiest method to add the patch
- Faster

##### Cons

- Can only support one platform and I have found a lot of people own the game on GOG, or can get it easier in certain countries that do not allow them to purchase the game.
- Certain Mods might not work unless you do a hybrid method also using root builder, as mod folders are a bit all over the place with this game.

### Root Builder

#### Pros

- Can support multiple platforms. Currently only:
  - GOG
  - Steam
- Can install mods to the root of the game folder so certain mods will work

#### Cons

- Can be much slower to launch the game if you try to run the full game or all the mods through it
- Harder to set up and work with

### Root Builder Setup and Info

Any mod or files in a mod that you want to go into the root of the game folder you would put inside a folder named "root" when setting up the mod.

### Unofficial Patch

When setting up the Unofficial Patch in the game, the process is a bit different than you would think.

1. Start by making sure the game is installed and then browse to the installation folder.
2. Grab the vampire.exe file, make a copy of it and paste it into a new folder, preferably close to the root of the drive.
   - This is because of the limited maximum path length in Windows.
   - So something like `C:\Temp`.
3. Download the Unofficial patch.
4. Double click to install the patch and then when it asks where you want it installed, change the path to the folder you set up in step 2.
   - This is done as the Unofficial Patch needs to patch the EXE of the game, but we don't want all the files and folders added to the stock game, as we will be adding them as a mod in Mod Organizer.
5. You need to pick the Core Version or the Plus Version
   1. Core is the Base Game
   2. Plus is Cut content from the game.
6. Once it finishes installing, open the folder that's selected and it should have a bunch of files and folders in it now.
7. We are going to add all the files in the `Root` to a Mod and then all the files inside `Unofficial_Patch` to another mod.
8. We are doing this so that we don't have all 1.2GB and 15,000 files load using root builder giving us a nice speed up.
9.  Create a new empty mod called something like `Unofficial Patch` in Mod Organizer.
   1. Create a new folder called `Root` inside this mod folder.
   2. Move all the files in the root (other than the `Unofficial_Patch` folder) into this mod.
10. Create a new empty mod called `Unofficial Patch`.
    1. Move all the files inside the `Unofficial_Patch` into this new mod folder.
11. Done.

### Reshade setup for the list

Follow these steps to set up and configure ReShade properly:

1. Prepare the Folder
    1.  Create a new folder with the name of the ReShade profile you want to make.
    2. Copy the following files into the new folder:
       - `LICENSE.md` - I have attached this here [LICENSE.md](/img/Files/LICENSE.md)
       - `vampire.exe` - This can be pulled from the Steam or GoG folder for the main game.
2. Step 2: Add the ReShade Configuration
   1. Download the ReShade preset you want to use (if you haven't already).
   2. Copy the `.ini` file for that preset into the folder you just created.
3. Step 3: Run ReShade Setup
   1. Launch **ReShade Setup** by running:
      - `ReShade_Setup_6.5.1_Addon.exe`
   2. Accept the warning screen by clicking **OK**.
   3. Click **Browse** and select the `vampire.exe` file you copied into the folder.
   4. Click **Next**.
   5. When prompted, select **DirectX 9**.
   6. Click **Next**.
   7. Click **Browse** again and select the `.ini` file you downloaded earlier.
   8. Continue clicking **Next** until the installation finishes, then close the setup tool.
4. Step 4: Clean Up
   1. Delete the temporary `vampire.exe` file from the folder.
   2. Open the `ReShade.ini` file in a text editor.
   3. Add the following settings or edit them to enable hotkeys for toggling effects and the overlay:
        ```ini
        [INPUT]
        ; Toggle all effects on/off
        KeyEffects=123,1    ; Control + F12

        ; Toggle the ReShade overlay on/off
        KeyOverlay=122,1    ; Control + F11
        ```
    4. Add a folder called `Root` to the mod folder and copy all the files inside it other than the metafile into it.

## Step 5: Wabbajack Compile Settings

When building the list in **Wabbajack**, you need to adjust the compile settings for the ReShade mods to ensure everything is included properly.

### Required Compile Settings

- **AlwaysEnable**
- **NoMatchInclude**

### Why These Are Important

- **AlwaysEnable**
  Ensures the mod is always included in the list, even if it is not checked by default.
  This way, players can still choose to enable it if they wish.

- **NoMatchInclude**
  Inlines all files that cannot be found in archives.
  This is why we added the `LICENSE.md` file — it guarantees that the build will include all necessary files, even if they aren't part of a recognized archive.

### ENB Settings for the list

```ini
[INPUT]
KeyUseEffect=123 ; Shift + F12
KeyBloom=120
KeyOcclusion=121
; ...
```

## Information on Modding the Game

### Editing the Main Menu

There are 3 parts to the main menu that I have found:

1. The Logo on top
2. The Particles that Float around the page and effects
3. The Background or Skybox

#### The Logo

The logo is 3 different files in `unofficial_patch\materials\interface\mainmenu\`:

1. `*.tth`
2. `*.ttz`
3. `*.vmt`

TTH stands for Troika Texture Header, and TTZ for Troika Texture Zipped. TTZ is where the actual bitmap is stored, and a `.vmt` file is a Valve Material Type file used by Valve's Source Engine to define the material properties of surfaces in video games, such as color, texture, and reflections. These files are typically text files that contain key-value pairs specifying various material attributes.

The easiest way to edit the file is to use a `.bat` file that the Unofficial Plus Patch includes in `SDK\SDKBinaries\tools\Texture Utils\` and simply drag the TTH file into the `TexConvert.bat`. Then edit the image using your favorite image editor and to convert it back into a `.tth` and `.ttz` just drag it into the `.bat` again.

You should not have to edit the .vmt unless you changed the name of the files but just naming the files the same as the .vmt is good enough.

#### The Particles

The particles are the objects bouncing or floating around the screen in the background, and the effects on the background like color overlays or things like smoke or fire effects.

The only ones I have edited are the floating images and they look to just be `mm_*.tga` files that are 128 x 128 in size and are located in `unofficial_patch\particles`.

> [!TIP]
> Converting all the TGA files to black will remove the image from displaying. This is handy if you want the background image to display.

If I edit the effects I will post more information, but nothing so far.

#### The Background or Skybox

The Skybox is in 2 places from what I can figure out with the following files:

1. `unofficial_patch\resource\`
   - `mainmenuparticles.txt`
     - This looks like where you set certain things about the skybox such as:
       - The Name of the Skybox
       - What Music plays
       - What the camera does and if you can do things like look around or have it rotate
       - What Particle Effects are loaded and more

2. `unofficial_patch\materials\skybox`
   - `mm_*.tth`
   - `mm_*.ttz`
   - `mm_*.vmt`
   - `mm_*bk.vmt`
   - `mm_*dn.vmt`
   - `mm_*ft.vmt`
   - `mm_*lf.vmt`
   - `mm_*rt.vmt`
   - `mm_*up.vmt`

   The TTH and TTZ are the same format but a larger size, probably 1024x1024 or 2048x2048 in size.
   
   **The naming convention for the files works out to be:**
   - bk = back (rear face of the cube)
   - ft = front (forward face)
   - lf = left (left face)
   - rt = right (right face)
   - up = top (ceiling face)
   - dn = down (bottom face)


Example of the `mainmenuparticles.txt`:

```json
MainMenuParticles
{
    camera_fov        "45"
    camera_near       "2"
    camera_far        "4096"
    camera_rotation   "0"
    default_skybox    "mm_skybox"


music             "music/vampire_theme.mp3" //(By @joylunamusic)


    Particle
    {
        emitter       "M_Clouds_Emmiter"
        origin        "[0,0,-30]"
        angle         "[0,0,0]"
    }


    Particle
    {
        emitter       "M_Clans_Emmiter"
        origin        "[0,0,-30]"
        angle         "[0,0,0]"
    }

    Particle
    {
        emitter       "M_Cels_Emmiter"
        origin        "[0,0,-30]"
        angle         "[0,0,0]"
    }


}
```

Example of the `mm_*.vmt`:

```json
"UnlitGeneric"
{
    "$basetexture"    "skybox/mm_f"
    "$basetexturetransform" "center .5 .5 scale 1.8 1.8 rotate 0 translate 0 0"
    "$detailscale" "1"
}
```