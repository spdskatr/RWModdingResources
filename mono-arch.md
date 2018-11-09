# Working with C&#35; RimWorld Mods on Arch Linux
Everything in this setup WorksOnMyMachine™, so I can't guarantee if it works on yours. A bit of ArchWiki and Google-fu might help solve any problems.

This article is a work in progress, I've outlined the basic steps in the section below.
## TL;DR
- **Set up MonoDevelop**
  - Install MonoDevelop via Flatpak
- **Set up ILSpy**
  - Download Zhentar's patch of ILSpy [here](https://github.com/Zhentar/ILSpy/releases)
  - Install WINE, Winetricks and `samba`
  - `winetricks dotnet40`

## Set up MonoDevelop

### Install MonoDevelop
You can always get MonoDevelop via the [AUR](https://aur.archlinux.org/packages/monodevelop-stable/), but various community members have reported it to be somewhat buggy (citation needed).

I installed MonoDevelop via flatpak:
```bash
# Omit --user to install system-wide, this way needs root privileges for obvious reasons
$ flatpak install --user --from https://download.mono-project.com/repo/monodevelop.flatpakref
```

Once installed, run:
```bash
$ flatpak run com.xamarin.MonoDevelop
```
to start MonoDevelop.

MonoDevelop should be able to open .sln files made with Visual Studio with no problems whatsoever.

ArchWiki: [Flatpak](https://wiki.archlinux.org/index.php/Flatpak), [Mono](https://wiki.archlinux.org/index.php/Mono)

## Set up ILSpy

Getting a decompiler to work on Linux is hard, especially since there are no decompilers that have been built for Linux (as of November 2018). You can, however, run ILSpy under Wine.

### Installing WINE and Winetricks
Follow the instructions on the [ArchWiki](https://wiki.archlinux.org/index.php/Wine).

### Get ILSpy
You can get a release of ILSpy for Windows from [the main repository](https://github.com/icsharpcode/ILSpy/releases), or [Zhentar's fork](https://github.com/Zhentar/ILSpy/releases) that implements better decompilation of iterators.

### Configuring WINE with Winetricks
You will need to install .NET Framework 4.0 to run ILSpy. Use this command to install .NET 4.0:
```bash
$ winetricks dotnet40
```

Make sure you also have the `samba` package installed from the official repositories to avoid [this](#ntlm_auth-code-vomit).

Once you have done both of these, try launching ILSpy with `wine /path/to/ILSpy.exe`.

ArchWiki: [Wine](https://wiki.archlinux.org/index.php/Wine), [Samba](https://wiki.archlinux.org/index.php/Samba)

### ntlm_auth code vomit
If you see something like this when you try to start up ILSpy:
```
System.Runtime.InteropServices.COMException: Unknown authentication source.
(Exception from HRESULT: 0x800706D3)
```
Chances are you'll probably also find a log message along the lines of:
```
0009:err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
```
For Arch, you will need to install the `samba` package.
