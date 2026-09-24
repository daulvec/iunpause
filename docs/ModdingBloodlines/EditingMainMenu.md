---
layout: default
title: Editing the main menu
parent: Modding Bloodlines
nav_order: 3
---

# {{ page.title }}

These notes describe the main menu files used by Bloodlines and the Unofficial Patch. Work on a copy of the files and test one change at a time in game. Paths below are relative to the game folder and may differ for other overhauls.

## Logo textures

The menu logo uses files under `unofficial_patch\materials\interface\mainmenu\`:

- `.tth` is the Troika texture header.
- `.ttz` contains the compressed texture data.
- `.vmt` is the material definition that points to the texture.

The Unofficial Patch includes `TexConvert.bat` under `SDK\SDKBinaries\tools\Texture Utils\`. Drag a copy of the `.tth` file onto the batch file to convert it for editing. After editing, drag the image onto the batch file again to create the game texture files. Keep the original texture name if you want to use the existing `.vmt`; if you rename it, update the material's texture path too.

## Particles and effects

Menu particle textures such as `mm_*.tga` are in `unofficial_patch\particles`. In the setup these notes were based on, the floating images used 128 × 128 textures. Making a texture black can hide that image and expose more of the background, but other particle effects may still be visible.

The menu's particle definitions and some scene settings are in `unofficial_patch\resource\mainmenuparticles.txt`. This example shows the settings and emitter structure; keep the entries your own menu needs:

```text
MainMenuParticles
{
    camera_fov        "45"
    camera_near       "2"
    camera_far        "4096"
    camera_rotation   "0"
    default_skybox    "mm_skybox"

    music             "music/vampire_theme.mp3"

    Particle
    {
        emitter       "M_Clouds_Emmiter"
        origin        "[0,0,-30]"
        angle         "[0,0,0]"
    }
}
```

## Skybox

Skybox materials are in `unofficial_patch\materials\skybox`. The `mm_*` `.tth` and `.ttz` files hold the textures, while the `.vmt` files define how they are displayed. The six skybox faces use these suffixes:

| Suffix | Face |
| --- | --- |
| `bk` | Back |
| `dn` | Down |
| `ft` | Front |
| `lf` | Left |
| `rt` | Right |
| `up` | Up |

A skybox material can look like this:

```text
"UnlitGeneric"
{
    "$basetexture"    "skybox/mm_f"
    "$basetexturetransform" "center .5 .5 scale 1.8 1.8 rotate 0 translate 0 0"
    "$detailscale" "1"
}
```

Check the texture paths in all six materials after replacing a skybox, then launch the game to check orientation and seams.
