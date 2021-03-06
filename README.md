# par2drive
Copyright Alberto Bursi <alberto.bursi@outlook.it>

This script is released under GPLv3 license.

this is a frontend for par2 command aka par2cmdline,
a tool that checksums and creates parity to recover corruption in files.
this frontend gives it an interface more suited for protecting data
in storage drives, as the par2 command itself was designed for protecting files
you upload to some sharing service, so it works like an archiver tool.

Since this is the 21st century, this script will work with folder
and file names with spaces too.

## SYNTAX
**par2drive action path**

### ACTION:
**sync** (updates parity files or creates parity files if not found)

**verify** (checks integrity of files with given parity files)

**scrub** (does a verify+repair)

**cleanup** (deletes all parity files of a file or recursively).

### PATH:
this script expects a path you want to work in, for example /home, but will work fine with a single file too.
If the path or file name contains spaces, please encase it with ", for example "/my folder" \n

## INSTALLATION

Download the script from this github repo directly and place it in your home folder with this command

**wget -O "$HOME"/par2drive https://raw.githubusercontent.com/bobafetthotmail/par2drive/master/par2drive**

Then make it executable

**chmod +x "$HOME"/par2drive**

Then execute it to see the help.

**"$HOME"/par2drive**

If your distro supports user-defined /bin in the home folder (afaik most do), move this script there
so it can be called directly from commandline.

**mkdir -p "$HOME"/bin**

**mv "$HOME"/par2drive "$HOME"/bin **

Afterwards (if the distro supports this) you can just call it with

**par2drive**


### LIMITATIONS:

Due to limitations in the POSIX shell I'm targeting with this script, it won't be able to deal with file or folder names containing
non-printable characters, which afaik should not be a huge issue anyway because I don't see any good reason to use such in your file name.

I did test it with random asian characters (ideograms), which are not ASCII but Unicode and it seems to still work fine.
I assume that the support for Unicode depends from the system, on Linux or *BSD distros it should always work.
On embedded devices (OpenWrt, DD-Wrt, a NAS or a modded router with Entware packages) it might require additional dependencies
to work with Unicode file names, please report if it's the case so I can add them to the checks at the beginning of the script.