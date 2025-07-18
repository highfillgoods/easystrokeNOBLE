# Installed on Ubuntu Noble 24.04 / Mint Mate 22
#  Easystroke - Nobile Fork 
## Prereq

sudo apt update && sudo apt install git build-essential autoconf automake libgtk2.0-dev libx11-dev libxtst-dev libpango1.0-dev libgtkmm-3.0-dev libdbus-glib-1-dev libboost-serialization-dev libxext-dev libxi-dev libxfixes-dev libxtst-dev gettext intltool xorg-dev xserver-xorg-dev intltool

## build and install
#download git

#make PREFIX=/usr

git clone https://github.com/highfillgoods/easystrokeNOBLE.git

cd easystrokeNOBLE

make

sudo make install

## to run easystroke run either or
/usr/local/bin/easystroke

easystroke

# Get EasyStroke to show in the Linux Start menu
sudo nano /usr/local/share/applications/easystroke.desktop
# find the following line:
Categories=GTK;Utility;Accessibility;
# Change it to:
Categories=GTK;Utility;Application;
---------------------------------------
ls -l /usr/local/share/applications/easystroke.desktop

desktop-file-validate /usr/local/share/applications/easystroke.desktop

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

sudo update-desktop-database

