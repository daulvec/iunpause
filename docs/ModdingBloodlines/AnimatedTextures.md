---
layout: default
title: Making animated textures
parent: Modding Bloodlines
nav_order: 2
---

# {{ page.title }}

This is a short workflow for adding an animated texture to Bloodlines. The [GameBanana animated texture tutorial](https://gamebanana.com/tuts/9544) covers creating an animated `.vtf` for Source. The steps below describe how to bring that texture into Bloodlines.

1. Create an animated `.vtf` using the GameBanana tutorial.
2. Run the `.vtf` through the Texture Converter in the [Bloodlines SDK](https://www.moddb.com/mods/vtmb-unofficial-patch/downloads/bloodlines-sdk) to make the Bloodlines texture files (`.tth` and `.ttz`). Put the converted files where the material expects its texture.
3. Open the existing `death.vmt` and add an `AnimatedTexture` proxy inside its material block. Keep the material's other settings. For a material whose base texture should animate, the proxy can look like this:

   ```text
   "Proxies"
   {
       "AnimatedTexture"
       {
           "animatedTextureVar" "$basetexture"
           "animatedTextureFrameNumVar" "$frame"
           "animatedTextureFrameRate" "24"
       }
   }
   ```

4. Adjust the frame rate to suit the animation, then launch the game and check the result.

If `death.vmt` already has a `Proxies` block, add `AnimatedTexture` inside that block instead of creating a second one. The material's `$basetexture` must point to the converted texture. See the [Valve Developer Community's material proxies reference](https://developer.valvesoftware.com/wiki/Material_proxies) for more on the proxy format.
