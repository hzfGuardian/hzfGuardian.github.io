

## Install Xilinx ISE 14.7 on Windows 10


* Fixing Project Navigator

 Note: I am assuming you are using ISE 14.7 and have installed it to the default location `C:\`

 1. Open the following directory: `C:\Xilinx\14.7\ISE_DS\ISE\lib\nt64`
 2. Find and rename `libPortability.dll` to `libPortability.dll.orig`
 3. Make a copy of `libPortabilityNOSH.dll` (copy and paste it to the same directory) and rename it `libPortability.dll`
 4. Copy `libPortabilityNOSH.dll` again, but this time navigate to `C:\Xilinx\14.7\ISE_DS\common\lib\nt64` and paste it there
 5. In `C:\Xilinx\14.7\ISE_DS\common\lib\nt64` Find and rename `libPortability.dll` to `libPortability.dll.orig`
 6. Rename `libPortabilityNOSH.dll` to `libPortability.dll`

* Fixing PlanAhead not opening from 64-bit Project Navigator

 PlanAhead will not open when you are running 64-bit Project Navigator (e.g. for I/O Pin Planning), it just displays the splash screen but never opens.

 To fix it, we have to force PlanAhead to always run in 32-bit mode.

 1. Open `C:\Xilinx\14.7\ISE_DS\PlanAhead\bin` and rename `rdiArgs.bat` to `rdiArgs.bat.orig`
 2. Download the new file [rdiArgs.bat](http://www.eevblog.com/forum/microcontrollers/guide-getting-xilinx-ise-to-work-with-windows-8-64-bit/?action=dlattach;attach=102040)
 3. Copy the new `rdiArgs.bat` file to `C:\Xilinx\14.7\ISE_DS\PlanAhead\bin`

 Now you should have a working ISE Design Suite on Windows 8.1/10 64-bit.

 Hope this helps!


