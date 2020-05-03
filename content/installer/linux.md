+++
title = "Install HandWriter on Linux"
showFullContent = true
+++
## Installing using the install script
Download the script
* If you use `curl` (default on Arch and its derivatives):
```bash
curl https://github.com/GDGVIT/HandWriter/raw/master/install.sh -o ~/handwriter-installer.sh -L
```
* If you use `wget` (default on Fedora, Ubuntu and their derivatives):
```bash
wget https://github.com/GDGVIT/HandWriter/raw/master/install.sh -O ~/handwriter-installer.sh
```
Execute the script
```bash
chmod a+x ~/handwriter-installer.sh
~/handwriter-installer.sh
```
You can remove the script once you're done.

If you would prefer to install the package manually, those instructions can be found [here](/installer/manual_install).