#Install Windows Fonts

1. Copy Windows ISO file to Download folder.
2. Run following commands
	* $ cd Downloads/
	* $ 7z e Windows.ISO sources/install.wim  ## Change the name of the ISO file accordingly
	* $ 7z e install.wim 1/Windows/{Fonts/"*".{ttf,ttc},System32/Licenses/neutral/"*"/"*"/license.rtf} -ofonts/
	* $ mkdir /usr/share/fonts/MSfonts
	* $ cp -r *.ttf /usr/share/fonts/MSfonts
	* $ fc-cache -f
3. Installation is Complete.

For more details visit:https://www.maketecheasier.com/install-microsoft-truetype-fonts-linux/
