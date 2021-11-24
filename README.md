# Guide to install old macOSX versions
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
