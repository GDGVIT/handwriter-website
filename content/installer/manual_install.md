+++
title = "Manually install on Linux"
showFullContent = true
+++

## Installing using the install script
```bash
curl https://github.com/GDGVIT/HandWriter/raw/master/install.sh -o ~/handwriter-installer.sh -L
chmod a+x ~/handwriter-installer.sh
~/handwriter-installer.sh
```
You can remove the script once you're done
```bash
rm ~/handwriter-installer.sh
```
## Installing manually

### Fedora
To manage HandWriter with Fedora's (or CentOS') package manager -
```bash
sudo rpm -v --import https://fbs.sh/SaurusXI/HandWriter/public-key.gpg
sudo dnf config-manager --add-repo https://fbs.sh/SaurusXI/HandWriter/rpm/HandWriter.repo
sudo dnf install handwriter
```
(On CentOS, replace 'dnf' by 'yum' and 'dnf config-manager' by 'yum-config-manager'.)
If HandWriter is already installed, you can force an immediate update via:
```bash
sudo dnf upgrade handwriter --refresh
```
Install fonts
```bash
curl https://github.com/GDGVIT/HandWriter/raw/master/assets/roboto.zip -o ~/roboto.zip -L
unzip ~/roboto.zip -d ~/roboto-font
mkdir ~/.local/share/fonts
cp ~/roboto-font/* ~/.local/share/fonts/
rm ~/roboto.zip && rm -r ~/roboto-font
```
This is for Fedora. For CentOS, use:
```bash
sudo yum clean all && sudo yum upgrade handwriter
```
Finally, you can also install without automatic updates by downloading from:
https://fbs.sh/SaurusXI/HandWriter/HandWriter.rpm

### Arch  
To manage HandWriter with pacman -
```bash
curl -O https://fbs.sh/SaurusXI/HandWriter/public-key.gpg && sudo pacman-key --add public-key.gpg && sudo pacman-key --lsign-key 29D5FDA07C763B56745B9E598AC59FA1ADE43023 && rm public-key.gpg
echo -e '\n[HandWriter]\nServer = https://fbs.sh/SaurusXI/HandWriter/arch' | sudo tee -a /etc/pacman.conf
sudo pacman -Syu handwriter
```
Install fonts
```bash
curl https://github.com/GDGVIT/HandWriter/raw/master/assets/roboto.zip -o ~/roboto.zip -L
unzip ~/roboto.zip -d ~/roboto-font
mkdir ~/.local/share/fonts
cp ~/roboto-font/* ~/.local/share/fonts/
rm ~/roboto.zip && rm -r ~/roboto-font
```
If HandWriter is already installed, you can force an immediate update via:
```bash
sudo pacman -Syu --needed handwriter
```
Finally, you can also install without automatic updates by downloading from:
https://fbs.sh/SaurusXI/HandWriter/HandWriter.pkg.tar.xz

### Debian and its derivatives (Ubuntu etc.)
To manage HandWriter with your package manager -
```bash
sudo apt-get install apt-transport-https
wget -qO - https://fbs.sh/SaurusXI/HandWriter/public-key.gpg | sudo apt-key add -
echo 'deb [arch=amd64] https://fbs.sh/SaurusXI/HandWriter/deb stable main' | sudo tee /etc/apt/sources.list.d/handwriter.list
sudo apt-get update
sudo apt-get install handwriter
sudo mv /opt/HandWriter/libz.so.1 /opt/HandWriter/libz.so.1.old
cd /opt/HandWriter/
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1
cd
``` 
Install fonts
```bash
wget https://github.com/GDGVIT/HandWriter/raw/master/assets/roboto.zip -O ~/roboto.zip -L
unzip ~/roboto.zip -d ~/roboto-font
mkdir ~/.local/share/fonts
cp ~/roboto-font/* ~/.local/share/fonts/
rm ~/roboto.zip && rm -r ~/roboto-font
```
If HandWriter is already installed, you can force an immediate update via:
```bash
sudo apt-get update -o Dir::Etc::sourcelist="/etc/apt/sources.list.d/handwriter.list" -o Dir::Etc::sourceparts="-" -o APT::Get::List-Cleanup="0"
sudo apt-get install --only-upgrade handwriter
```
*Why the symlink?* <br>
For maximum portability, the debian package was built in an Ubuntu 16.04 environment. However, this leads to a known [issue](https://ubuntuforums.org/showthread.php?t=2375927) with systems based on Ubuntu 17.10 or newer. <br><br>
You can also install without automatic updates by downloading from:
    https://fbs.sh/SaurusXI/HandWriter/HandWriter.deb <br>
After installing the package, remember to create the symlink - 
```bash
sudo mv /opt/HandWriter/libz.so.1 /opt/HandWriter/libz.so.1.old
cd /opt/HandWriter/
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1
cd
```