# Finding AES Key
Some games will have their `.pak` files encrypted with an AES key. </br>
Luckily, it's an easy task to find the AES key.

## Getting the AES
1. Download the [AES_Finder.exe](https://github.com/Dmgvol/UE4_Modding/raw/master/Tools/AES_finder.exe).<br>
_(the tool is using Java, and requires Java Runtime to be installed)_
2. Place the `.exe` in the same folder as the game binary executable.<br>
_(the one with "Win64-Shipping.exe" in its name)_<br>
(For example: `...\Ghostrunner 2\Ghostrunner2\Binaries\Win64\`)
3. Launch the game and then launch the AES finder.
4. Wait a few seconds, and a new text file named `key.txt` will appear in that folder, which will contain the AES key.


That's it!