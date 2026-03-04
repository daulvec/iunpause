---
layout: default
title: Common Issues
parent: Fashionista
nav_order: 6
has_children: false
has_toc: true
---

# Contents
{: .no_toc}

1. TOC
{:toc}

# Common Issues

Here you find solution to common game issues.  
Please read through this file before asking questions in discord.

## Could not find vampire.exe
... at the path configured in ModOrganizer.ini

If you encounter the error depicted here
![Image](/media/img/Fashion/CommonIssues/vampire-exe-not-found.png)
...click on "Settings" in the top navigation menu.
Navigate to the "Paths" tab and make sure the path in the "Managed Game" field points to your actual install folder and to the correct path for vampire.exe, like depicted below.
![Image](/media/img/Fashion/CommonIssues/vampire-exe-game-path.png)

## Borderless / Window / Fullscren

Well, first of all, let me destroy your hopes and dreams; there is no borderless fullscreen.  
It's an old game.  

But if you want to swtich from window to fullscreen or vice versa, you can do this:  

1. Go the the MO2 Folder
2. Open the Profiles Folder
3. Open the Fashionista Folder
4. Open Bloodlines.ini
5. Change the `Arguments= -game Unofficial_Patch -window` Line to `Arguments= -game Unofficial_Patch -fullscreen`

Its the Same Process to edit any Profile you want to run