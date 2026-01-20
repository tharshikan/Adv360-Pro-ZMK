# Karabiner Elements Configuration

This directory contains the `karabiner.json` configuration for this setup.

## How to use (Symlink Strategy)
To ensure this repository always tracks your active configuration, delete your local config and replace it with a symlink to this file.

**Run this command in your terminal:**
```bash
# Backup existing config just in case
mv ~/.config/karabiner/karabiner.json ~/.config/karabiner/karabiner.json.bak

# Link this repo's file to the system location
# (Replace [REPO_PATH] with the actual path to this folder)
ln -s "$(pwd)/karabiner.json" ~/.config/karabiner/karabiner.json
```

## Why do this?
*   **Version Control:** Your Mac-side remappings are now saved alongside your ZMK firmware.
*   **Portability:** Clone this repo on a new Mac, run the symlink command, and your setup is restored.
