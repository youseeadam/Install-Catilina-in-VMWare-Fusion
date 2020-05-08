# Install-Catilina-in-VMWare-Fusion
How to install Catalina 
Download the Catalina installer from https://apps.apple.com/us/app/macos-catalina/id1466841314?mt=12

hdiutil create 1015.dmg -size 8g -layout SPUD -fs HFS+J
hdiutil attach 1015.dmg -noverify -nobrowse -mountpoint /Volumes/InstallCatalina
sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/InstallCatalina
hdiutil detach /Volumes/Install\ macOS\ Catalina\ Beta
hdiutil resize -sectors min 1015.dmg
