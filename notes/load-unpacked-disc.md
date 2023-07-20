# Load Unpacked disc

Repacking data back into a disc file is surely taking time, especially how big the file size is.

Luckily we can load the unpacked disc directly into the game, so this can save our time when testing the mod.

## How this trick work?

The game has check this following path for its data:
- ./disc
- ../../../DATA/resource_win/disc
- ../../../DATA/resource_win/disc_test/

Path that end with `/` is a folder.

So the game will try load that list in order.

## Moving unpacked disc

First, we need to move the unpacked disc to the required path.

### Steam game

If you are using "steam" game version, you need to locate where the original `STORY OF SEASONS A Wonderful Life.exe`.

- If you have a desktop shortcut for the game, right-click on that shortcut, then click **Open file location**.
- You don't have the desktop shortcut, so use the start menu to find "Story of season", if the game is shown in the result, right-click on that item then click **Open file location**.

An explorer will open in the original `STORY OF SEASONS A Wonderful Life.exe` folder.

From there, go up 3 folders then create `DATA/resource_win/disc_test` folder.

Finally, put your unpacked disc there.

### Non-steam game

If you are using "non-steam" game version, you just need to move the game into the root folder of the disk.

For example, when the game folder is in `C:` disk, then move it into `C:\sos-awl-game` or something like that, as long as it is in the root of the disk.

Then create a new folder in `C:\DATA\resource_win\disc_test`

Finally, put your unpacked disc there.

## Delete `disc` file

Or... We can just rename it to something else, for example, `not_disc` or `disc.bak` or whatever except `disc`.

This is required to make sure the game does not load that `disc` file and use alternative disc data.

## Another tips

Instead of putting all data in that folder, you can link your unpacked disc folder with the required folder.

The command is (I use PowerShell to run this, not tested in another shell):

```powershell
new-item -Type Junction -Path C:\DATA\resource_win\disc_test\ -Target C:\path\to\your\unpacked\disc\
# or
new-item -Type Junction -Path ..\..\..\DATA\resource_win\disc_test\ -Target C:\path\to\your\unpacked\disc\
```
