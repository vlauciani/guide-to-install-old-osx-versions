# Guide to install old macOSX versions - bootable USB key
This guide is base on macOSX Yosemite but works on others versions.

## Prepare USB key
Launch *Disk Utility*, choose the USB key and *Erase*; set:
- **Name**, to *Untitled*
- **Format**, to *Mac OS Extended (Journaled)*

## Get old versions of macOS
Get old version from here:
- https://support.apple.com/en-us/HT211683

this will download `InstallMacOSX.pkg` file.

## Extracting the Installer
Create a working dir:
```
cd ~/Desktop
mkdir -p MacInstall/extract
```

Mount the `InstallMacOSX.dmg` (doubble click) and then:
```
cd ~/Desktop/MacInstall
cp /Volumes/Install\ OS\ X/InstallMacOSX.pkg .
```

## Create app
```
cd ~/Desktop/MacInstall/extract
xar -xf ~/Desktop/MacInstall/InstallMacOSX.pkg
cd InstallMacOSX.pkg
tar xvzf Payload
mv InstallESD.dmg Install\ OS\ X\ Yosemite.app/Contents/SharedSupport
mv Install\ OS\ X\ Yosemite.app /Applications
```

## Create USB bootable key
```
sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ Yosemite.app
```

## Use the bootable installer (Intell processor)
- Plug the bootable installer into a Mac that is connected to the internet and compatible with the version of macOS you're installing.
- Press and hold the Option (Alt) ⌥ key immediately after turning on or restarting your Mac.
- Release the Option key when you see a dark screen showing your bootable volumes.
- Select the volume containing the bootable installer. Then click the up arrow or press Return.

**!!! NOTE !!!**: If you are receiving the message:

<img width="419" alt="E1BMF" src="https://user-images.githubusercontent.com/16477095/143209841-cd807bb0-d788-4b3a-b9b9-da8a658468de.png">

try to bypass the security check in *Utilities* -> *Terminal*:
```
-bash-3.2# installer -pkg /Volumes/Mac\ OS\ X\ Install\ DVD/Packages/OSInstall. mpkg -target /Volumes/Macintosh\ HD/
```

---
before to start the installer, in the first install page go to *Utilities* -> *Terminal* and set the the date using the command `data` with options:
```
MM - 2 digit month  01 - 12
DD - 2 digit date   01 - 31
HH - 2 digit hour   01 - 24
mm - 2 digit minute 01 - 59
YY - 2 digit year   > 15
```
for example date *24-Nov-2021 11:11:00*:
```
-bash-3.2# date 1124101121
Wed Nov 24 10:11:00 PST 2021
-bash-3.2#
```

once that is done go through the install normally.
