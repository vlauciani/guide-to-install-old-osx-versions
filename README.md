# guide-to-install-old-osx-versions
A simple guide to install old OSX versions.

this guide is base on macOSX Yosemite but works on others versions.

## Prepare USB key


## Get old versions of macOS
Get old version from here:
- https://support.apple.com/en-us/HT211683

## Extracting the Installer
Create a wrking dir:
```
cd ~/Desktop
mkdir -p MacInstall/extract
```

Mount the `InstallMacOSX.dmg` (doubble click) and then:
```
cd ~/Desktop/MacInstall
cp /Volumes/Install\ OS\ X/InstallMacOSX.pkg .
```

## Create USB bootable key
```
cd ~/Desktop/MacInstall/extract
xar -xf ~/Desktop/MacInstall/InstallMacOSX.pkg
cd InstallMacOSX.pkg
tar xvzf Payload
mv InstallESD.dmg Install\ OS\ X\ Yosemite.app/Contents/SharedSupport
mv Install\ OS\ X\ Yosemite.app /Applications
sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ Yosemite.app
```
