# Finding AES Key
Some games will have their `.pak` files encrypted with an AES key. </br>
Luckily, it's an easy task to find the AES key.

There are two methods:
- Method 1: using [AESKeyFinder](https://github.com/GHFear/AESKeyFinder-By-GHFear) by [GHFear](https://github.com/GHFear/)
- Method 2: using the Java version Aes_Finder (backup if first doesn't work).

## Getting the AES - Method 1
1. Navigate to [AESKeyFinder](https://github.com/GHFear/AESKeyFinder-By-GHFear).
2. Download as zip, by clicking on the `Code` dropdown and clicking on `Download ZIP`.
3. Once you extract the zip file, drop your game's largest executable (usually called "Gamename"-Shipping.exe) into the folder containing the scripts.
4. Launch `Find_AES_Key.bat` and follow the instructions on the screen.
5. Within a few seconds, it will output the found AES key on the screen.




## Getting the AES - Method 2
1. Download the [AES_Finder.exe](https://github.com/Dmgvol/UE_Modding/raw/main/Tools/AES_finder.exe).<br>
_(the tool is using Java, and requires Java Runtime to be installed)_
2. Place the `.exe` in the same folder as the game binary executable.<br>
_(the one with "Win64-Shipping.exe" in its name)_<br>
(For example: `...\Ghostrunner 2\Ghostrunner2\Binaries\Win64\`)
3. Launch the game and then launch the AES finder.
4. Wait a few seconds, and a new text file named `key.txt` will appear in that folder, which will contain the AES key.


That's it!