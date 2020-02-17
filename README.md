# RimworldModSkip11LogMessage

Mods that have been updated to 1.1 will give some log messages, but they are not errors, just tags that 1.0 can't recognize. This mod just make it skip a few of those tags.

![Mod](https://raw.githubusercontent.com/purpleorangegames/RimworldModSkip11LogMessage/master/screenshotCode.png)

I made two versions, one checks for two tags (supportedGameVersions and packageId), can add more if necessary.

The second skips this particular log call, so any tag errors are surpressed, so it is future proof but could suppress genuine errors from other mods.


To use bsdiff download it from here: https://www.pokorra.de/coding/bsdiff.html

1. To use go to (Steam\steamapps\common)\RimWorld\RimWorldWin64_Data\Managed

2. Copy bspatch to that folder, open a cmd and navigate there

3. bspatch.exe Assembly-CSharp.dll newfile.dll Assembly-CSharp_log_removed_PATCH.diff

4. Then backup Assembly-CSharp.dll as the original file

5. Rename newfile.dll to Assembly-CSharp.dll


IMPORTANT: If you want use can run the bat file provided instead of step 3-5
