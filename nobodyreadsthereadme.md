# Readme

## Quicktest

A relevant excerpt of the readme is reproduced below:

A partial source release is included with the game in the Source folder.
Here you'll find a few of the source files for the base game for your reference.

For testing, you can start the game into a tiny (fast-loading) map with one click by running the game with the -quicktest command line parameter. For example:

    C:/RimWorld/RimWorld.exe -quicktest

If you're a modder, we recommend making a shortcut to the game that does this.

## Savedata

You can override the save data folder. This is useful, for example, if you want to install the game on a USB stick so you can plug and play it from anywhere.
To do this, add this to the end of the command line used to launch the game:

    -savedatafolder=C:/Path/To/The/Folder

So it'll look something like this:

   C:/RimWorld/RimWorld.exe -savedatafolder=C:/Path/To/The/Folder

If you don't start the path with anything, it'll be relative to the game's root folder. So you could do this, to have the game save data in a folder called SaveData in its own root folder:

    -savedatafolder=SaveData

Be sure the game is running with permission to modify the folder. It may not work properly if, for example, you run the game under default permissions on its own install folder.

## EULA

There's a EULA.txt supplied with the game. Read it. It's understandable and contains good information. Know your rights and limits. Local laws may differ. We are not lawyers.