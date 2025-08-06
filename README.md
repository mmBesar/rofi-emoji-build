# rofi-emoji - Debian Packages

[![Build Status](https://github.com/mmBesar/rofi-emoji-build/actions/workflows/sync-upstream.yml/badge.svg)](https://github.com/mmBesar/rofi-emoji-build/actions)
[![Latest Release](https://img.shields.io/github/v/release/mmBesar/rofi-emoji-build)](https://github.com/mmBesar/rofi-emoji-build/releases/latest)

**Unofficial Debian packages** for [rofi-emoji](https://github.com/Mange/rofi-emoji) - An emoji selector plugin for Rofi.

> **⚠️ Important:** This repository only provides Debian packaging. All credit for rofi-emoji goes to the original developer [Magnus Bergmark](https://github.com/Mange/rofi-emoji).

## About

This repository automatically builds Debian packages from the official [Mange/rofi-emoji](https://github.com/Mange/rofi-emoji) repository. The packages are built automatically when new upstream tags are available.

### Features

- 🔍 **Search emojis** by name, keywords, or category  
- 📋 **Copy to clipboard** with xclip/xsel/wl-clipboard support
- ⌨️ **Direct insertion** into focused applications
- 🏷️ **Filter by groups** (@symbols) and subgroups (#mammal)
- 🎨 **Customizable format** and theming
- 🖥️ **X11 and Wayland** compatible
- 📦 **Multi-Debian support** (Bookworm, Trixie, Sid)
- 🔄 **Automatic upstream sync**

## Quick Installation

### Prerequisites
```bash
sudo apt update
sudo apt install curl rofi
```

### Debian 12 (Bookworm)
```bash
wget $(curl -s https://api.github.com/repos/mmBesar/rofi-emoji-build/releases/latest | grep "browser_download_url.*bookworm.*\.deb" | grep -v "dbgsym" | cut -d '"' -f 4)
sudo apt install ./rofi-emoji_*bookworm*.deb
```

### Debian 13 (Trixie)
```bash
wget $(curl -s https://api.github.com/repos/mmBesar/rofi-emoji-build/releases/latest | grep "browser_download_url.*trixie.*\.deb" | grep -v "dbgsym" | cut -d '"' -f 4)
sudo apt install ./rofi-emoji_*trixie*.deb
```

### Debian Sid (Unstable)
```bash
wget $(curl -s https://api.github.com/repos/mmBesar/rofi-emoji-build/releases/latest | grep "browser_download_url.*sid.*\.deb" | grep -v "dbgsym" | cut -d '"' -f 4)
sudo apt install ./rofi-emoji_*sid*.deb
```

## Manual Installation

1. Go to the [Releases page](https://github.com/mmBesar/rofi-emoji-build/releases/latest)
2. Download the appropriate `.deb` file for your Debian version:
   - `rofi-emoji_*~bookworm*.deb` for Debian 12
   - `rofi-emoji_*~trixie*.deb` for Debian 13
   - `rofi-emoji_*~sid*.deb` for Debian Sid
3. Install: `sudo apt install ./rofi-emoji_*.deb`

## Usage

### Basic Usage
```bash
# Launch emoji selector
rofi -modi emoji -show emoji

# With custom copy keybind (Ctrl+C)
rofi -modi emoji -show emoji -kb-custom-1 Ctrl+c

# Copy mode only (no insertion)
rofi -modi emoji -show emoji -emoji-mode copy
```

### Search Examples
- Type emoji names: `laugh`, `heart`, `fire`
- Search by keywords: `animal`, `food`, `flag`
- Filter by group: `@sym` (symbols), `@people` (smileys & people)
- Filter by subgroup: `#mammal`, `#food-fruit`

### Keyboard Shortcuts
| Key | Action |
|-----|---------|
| `Enter` | Select emoji (copy + insert) |
| `Shift+Enter` | Open emoji menu with options |
| `Alt+1` (or custom) | Copy emoji to clipboard |

## Configuration

### Dependencies
- **Required**: `rofi`
- **Clipboard** (pick one): `xclip`, `xsel`, or `wl-clipboard`
- **Insertion** (optional): `xdotool` (X11) or `wtype` (Wayland)

### Install clipboard tools
```bash
# For X11
sudo apt install xclip

# For Wayland  
sudo apt install wl-clipboard

# For insertion support
sudo apt install xdotool  # X11
sudo apt install wtype    # Wayland
```

### Custom Configuration
Create `~/.config/rofi/config.rasi` and add:
```rasi
configuration {
  modi: "drun,emoji,window,run";
  kb-custom-1: "Control+c";  // Custom copy shortcut
}
```

## Troubleshooting

### Package Conflicts
If you have other rofi-emoji packages installed:
```bash
sudo apt remove rofi-emoji
sudo apt install ./rofi-emoji_*.deb
```

### Missing Dependencies
If you get dependency errors:
```bash
sudo apt install -f
```

### Plugin Not Loading
Check if rofi can find the plugin:
```bash
rofi -dump-config | grep -i plugin
```

### Clipboard Issues
Test clipboard tools:
```bash
# Test xclip
echo "test" | xclip -selection clipboard

# Test wl-clipboard (Wayland)
echo "test" | wl-copy
```

## Repository Structure

- **`upstream` branch**: Synced automatically from [Mange/rofi-emoji](https://github.com/Mange/rofi-emoji)
- **`main` branch**: Contains Debian packaging files
- **Workflows**: Automatic sync and build processes
- **Releases**: Built `.deb` packages for multiple Debian versions

## Building from Source

If you want to build the packages yourself:

```bash
git clone https://github.com/mmBesar/rofi-emoji-build.git
cd rofi-emoji-build
# GitHub Actions will automatically build on push/tag
```

## License and Attribution

### This Repository (Packaging)
- **License:** MIT License
- **Copyright:** 2025 mmBesar
- **Purpose:** Debian packaging only

### Original rofi-emoji Project
- **Repository:** [Mange/rofi-emoji](https://github.com/Mange/rofi-emoji)
- **License:** MIT License  
- **Copyright:** 2020-2024 Magnus Bergmark
- **All credit for rofi-emoji functionality goes to the original developer**

### Important Legal Notes

- This repository **only provides packaging** - no modifications to rofi-emoji source code
- All rofi-emoji functionality, features, and code belong to the original [Mange/rofi-emoji](https://github.com/Mange/rofi-emoji) project
- We build directly from the official upstream repository
- This is an **unofficial** packaging effort, not affiliated with the rofi-emoji developer
- If you encounter bugs with rofi-emoji functionality (not packaging), please report them to the [upstream repository](https://github.com/Mange/rofi-emoji/issues)

## Support

### For rofi-emoji Issues (Functionality, Features, Bugs)
- **Official Repository:** https://github.com/Mange/rofi-emoji
- **Official Issues:** https://github.com/Mange/rofi-emoji/issues

### For Packaging Issues (Installation, Dependencies, Debian-specific)
- **This Repository Issues:** https://github.com/mmBesar/rofi-emoji-build/issues
- **Discussions:** Use GitHub Discussions for questions

## Contributing

Contributions to the **packaging** are welcome:
- Improve Debian packaging scripts
- Fix dependency issues  
- Enhance documentation
- Test on different Debian versions

**Do not** report rofi-emoji functionality issues here - those belong in the upstream repository.

## Acknowledgments

- **Magnus Bergmark** for creating and maintaining [rofi-emoji](https://github.com/Mange/rofi-emoji)
- **Dave Davenport** and contributors to [Rofi](https://github.com/davatorium/rofi)
- The **Debian** community for packaging standards and tools

## Disclaimer

This is an **unofficial** packaging project. Use at your own risk. The maintainer is not responsible for any issues arising from the use of these packages. Always backup your system before installing unofficial packages.

For production environments, consider building from source following the [official installation guide](https://github.com/Mange/rofi-emoji#compile-from-source).
