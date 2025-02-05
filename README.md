# Installed on Ubuntu Mate 24.04 
## Prereq

sudo apt update && sudo apt install git build-essential autoconf automake libgtk2.0-dev libx11-dev libxtst-dev libpango1.0-dev libgtkmm-3.0-dev libdbus-glib-1-dev libboost-serialization-dev libxext-dev libxi-dev libxfixes-dev libxtst-dev gettext intltool xorg-dev

## build and install
download git

cd easystroke

make PREFIX=/usr

sudo make install

## to run easystroke run
/usr/local/bin/easystroke


### Despite numerous build warnings, it produced the executable easystroke. This progress indicates a successful build.
