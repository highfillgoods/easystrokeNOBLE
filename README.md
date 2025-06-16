# Easystroke

> **Note**: This is a fork of the original Easystroke project, updated for compatibility with Ubuntu 24.04 Noble Numbat. This README is mostly AI-generated, can contain errors.

**A gesture-recognition application for X11 that allows you to control your desktop using mouse gestures.**

Easystroke is a powerful and intuitive gesture recognition tool that enables you to execute commands, send keystrokes, control applications, and perform various desktop actions through simple mouse movements. Draw gestures with your mouse, trackpad, or stylus to trigger customizable actions.

## Features

- **Gesture Recognition**: Advanced stroke matching algorithm with configurable sensitivity
- **Application-Specific Gestures**: Different gesture sets for different applications
- **Multiple Action Types**:
  - Execute shell commands
  - Send keyboard shortcuts
  - Type text
  - Scroll and button actions
  - Window management (minimize, unminimize, show/hide)
- **Visual Feedback**: Customizable stroke visualization with multiple themes (fire, water, composite effects)
- **Device Support**: Full XInput2 support for mice, trackpads, tablets, and styluses
- **Timeout Gestures**: Execute actions based on holding gestures
- **Click & Hold**: Special gesture mode for extended interactions
- **Internationalization**: Supports 16 languages

## Installation

### Prerequisites

**Ubuntu/Debian:**
```bash
sudo apt update && sudo apt install git build-essential autoconf automake \
    libgtk2.0-dev libx11-dev libxtst-dev libpango1.0-dev libgtkmm-3.0-dev \
    libdbus-glib-1-dev libboost-serialization-dev libxext-dev libxi-dev \
    libxfixes-dev libxtst-dev gettext intltool xorg-dev
```

**Required Dependencies:**
- gtkmm-3.0
- dbus-glib-1  
- boost_serialization
- X11, Xext, Xi, Xfixes, Xtst
- Build tools (make, gcc/g++)

### Building from Source

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd easystroke
   ```

2. **Build the application:**
   ```bash
   make PREFIX=/usr
   ```

3. **Install:**
   ```bash
   sudo make install
   ```

4. **Run:**
   ```bash
   /usr/local/bin/easystroke
   ```

### Build Options

```bash
# Clean build artifacts
make clean

# Create distribution tarball
make tarball

# Generate .clang_complete for IDE support
make complete

# Update translations
make update-translations
```

## Usage

### Getting Started

1. **Launch Easystroke**: Run `/usr/local/bin/easystroke` or find it in your applications menu
2. **Access Settings**: Click the system tray icon to open preferences
3. **Create Gestures**: 
   - Click "Add Action" to create a new gesture
   - Select action type (Command, Key, Text, etc.)
   - Draw your gesture in the gesture area
   - Configure the action details

### Action Types

- **Command**: Execute shell commands
- **Key**: Send keyboard shortcuts (e.g., Ctrl+C, Alt+Tab)
- **Text**: Type predefined text
- **Button**: Simulate mouse clicks
- **Scroll**: Scroll up/down or left/right
- **Misc**: Special actions (minimize, unminimize, disable/enable easystroke)

### Advanced Features

- **Application-Specific Gestures**: Create different gesture sets for specific applications
- **Modifier Keys**: Gestures can be triggered with modifier combinations
- **Timeout Profiles**: Adjust gesture recognition timing
- **Visual Themes**: Choose from multiple stroke visualization styles
- **Device Configuration**: Configure specific input devices
- **Right-click + scroll action**: Instead of a gesture, Right-click + scroll up/down can be used. 
      A possible usage is to emulate volumouse (Win app) by associating a command to increase/reduce the volume.

### Command Line Options

```bash
easystroke [OPTIONS]

Options:
  -c, --config     Start with configuration window open
  -g, --gui        Start with configuration dialog
  -d, --debug      Enable debug output
  -h, --help       Show help message
```

## Configuration

Configuration files are stored in `~/.easystroke/` and include:

- **Gestures**: `~/.easystroke/actions-0.5.6`
- **Preferences**: `~/.easystroke/preferences-0.5.5`

Settings can be modified through the GUI or by editing these files directly.

## System Requirements

- **X11 Server**: Version 1.7 or higher (XInput2 support required)
- **Desktop Environment**: Any X11-based environment
- **Architecture**: Works on all major Linux architectures

## Troubleshooting

### Common Issues

1. **Gestures not recognized**: Check XInput2 support and device permissions
2. **Visual effects not working**: Install composite manager (like Compiz)
3. **Application detection issues**: Verify window manager compatibility

### Build Warnings

The build process may generate warnings but should still produce a functional executable. These warnings are generally harmless for normal operation.

### Debug Mode

Enable debug output by creating `debug.mk` based on `debug.mk.ex` for additional troubleshooting information.

## Development

### Architecture

- **Event Handling**: Chain of responsibility pattern with Handler classes
- **Gesture Recognition**: Dynamic programming algorithm in stroke.c
- **Action System**: Hierarchical database with boost::serialization
- **UI Framework**: GTKmm 3.0 with Glade interface definitions

### Key Files

- `main.cc`: Application entry point
- `handler.cc`: Core event handling logic  
- `stroke.c`: Gesture matching algorithm
- `actions.cc`: Action execution
- `win.cc`: Main configuration window
- `gui.glade`: UI layout definitions

## Version History

**Current Version**: 0.6.1 (December 2024)
- Ubuntu 24.04 Noble Numbat compatibility fixes (Carson Highfill)
- Fixed TreeView row highlighting in actions tab
- Fixed Misc type action Details dropdown issues
- Fixed stroke serialization for gesture coordinate saving/loading
- Modernized build system and dependencies
- Comprehensive documentation overhaul

See `changelog` file for complete version history.
