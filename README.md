# Skip 1.1 mod log messages for 1.0 Rimworld

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

You can download them here:

https://github.com/purpleorangegames/RimworldModSkip11LogMessage/releases


# Do it yourself with dnSpy

1. Download dnSpy: https://github.com/0xd4d/dnSpy/releases

2. Backup (Steam\steamapps\common\)RimWorld\RimWorldWin64_Data\Managed\Assembly-CSharp.dll

3. Open dnSpy, click File -> Open (or Ctrl+O) and select Assembly-CSharp.dll

4. Click Edit -> Search Assemblies (or Ctrl+Shift+K) and write ObjectFromXml, select the only entry that appears

5. You should be seeing the code from the method we want to change now,
right click on it and choose Edit Method C# ... (or Ctrl+Shift+E)

6. Press Ctrl+F and type: to any field

7. Now you can either remove the Log call or make an if with the selected tags, here is original method:
'''Log.Error(string.Concat(new string[]
									{
										"XML error: ",
										xmlNode.OuterXml,
										" doesn't correspond to any field in type ",
										t3.GetType().Name,
										". Context: ",
										xmlRoot.OuterXml
									}), false);'''
                  
8. After you are done press the Compile button on the bottom right of the window

9. Click File -> Save Method...

10. Click Ok and it will overwrite the original file, remember to make a backup of it first (#2)

Now just run Rimworld 1.0 and you won't see more message logs from updated 1.1 mods.
