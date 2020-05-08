# Install-Catilina-in-VMWare-Fusion
How to install Catalina 
Download the Catalina installer from https://apps.apple.com/us/app/macos-catalina/id1466841314?mt=12
<p>
hdiutil create 1015.dmg -size 8g -layout SPUD -fs HFS+J<br />
hdiutil attach 1015.dmg -noverify -nobrowse -mountpoint /Volumes/InstallCatalina<br />
sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/InstallCatalina<br />
hdiutil detach /Volumes/Install\ macOS\ Catalina<br />
hdiutil resize -sectors min 1015.dmg<br />
</p>
<p>
Now Open VMWare Fusion</ br>
Mount the DMG and drag the .app onto fusion, this will start the installer.<br>
At the Finish page click the Customize Settings, this will get everything ready, but will not turn on the VM. If you click Finish it will start</br>
DO NOT turn on the machine once you finished the wizard. Make the following changes</br>
<ol>
  <li>Edit the VMX of the machine</li>
  <li>In the virtual machine library right click on the virtual machine and click on Show in Finder</li>
  <li>right click on the VMX file and choose Package COntents</li>
  <li>Edit the VMX file with Text Editor</li>
  <li>add the following after the .encoding line (I like to put it after thVirtualHW.version number
    <blockquote>
      hw.model = "Macmini8,1"</br>
    Macmini8,1= "MacMini"</br>
    serialNumber="TheSerialNubmerOfYouMachineChnaging1Character"</br>
serialNumber.reflectHost = "FALSE"</br>
hw.model.reflectHost = "FALSE"</br>
smbios.reflectHost = "FALSE"</br>
    </blockquote>
  </li>
  </ol>
  How to get the information above
  <ul>
  <li>Serial Number: system_profiler SPHardwareDataType | grep Serial </li>
  <li>hw.model: system_profiler SPHardwareDataType | grep "Model Identifier"</li>
  <li>The last one should match the hw.model value = The simple display Name (It can be whatever), but to get technical: system_profiler SPHardwareDataType | grep "Model Name"
    </lI>Now to be really simple you can just go to About this Mac-->System Report and it is listed under the ver first thing, Hardware, but command line is more fun</li>
    </ul>
 <p>
  <B>SAVE THE FILE</B>
  </p><p>
  Now go to the settings of the virtual machine (right click settings), then go to Network adapter and choose a bridged Networking option, one of the green ones.
  </p>
  <B>Now turn on the machine and go through the setup process.</B>
  <p>You may get an error on first boot about ""FALSE"" that is okay, it is just fixing how something was copied and pasted.</p>
  <B>Before you login for the first time SHUTDOWN the computer</B> then start it back up and you should be all set
    
