# Building .deb Package

This project includes Debian packaging support for easy installation on Ubuntu/Debian systems.

## Prerequisites

Install the required build tools:

```bash
sudo apt update
sudo apt install debhelper help2man dpkg-dev
```

Make sure you also have the build dependencies:

```bash
sudo apt install libgtkmm-3.0-dev libdbus-glib-1-dev libboost-serialization-dev \
                 libx11-dev libxext-dev libxi-dev libxfixes-dev libxtst-dev \
                 pkg-config intltool
```

## Building the Package

Simply run:

```bash
make deb
```

This will:
1. Check for required build tools
2. Build the .deb package using `dpkg-buildpackage`
3. Place the resulting .deb file in the parent directory

## Installing the Package

After successful build, install with:

```bash
sudo dpkg -i ../easystroke_*.deb
```

If there are dependency issues, fix them with:

```bash
sudo apt install -f
```

## Package Information

- **Package name**: `easystroke`
- **Version**: Based on git describe (currently 0.6.0-26)
- **Architecture**: Any (will build for your current architecture)
- **Dependencies**: Automatically detected runtime dependencies

## Files Included

The package includes:
- `/usr/bin/easystroke` - Main executable
- `/usr/share/icons/hicolor/scalable/apps/easystroke.svg` - Application icon
- `/usr/share/applications/easystroke.desktop` - Desktop entry
- `/usr/share/locale/*/LC_MESSAGES/easystroke.mo` - Translation files
- `/usr/share/man/man1/easystroke.1.gz` - Manual page