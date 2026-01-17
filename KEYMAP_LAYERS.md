# Kinesis Adv360 Pro - Keymap Layers Documentation

This document provides a comprehensive visual reference for all keyboard layers configured in this ZMK firmware.

## Table of Contents
- [Layer Overview](#layer-overview)
- [Layer Access](#layer-access)
- [Layer 0: Base Layer](#layer-0-base-layer)
- [Layer 1: Keypad Layer](#layer-1-keypad-layer)
- [Layer 2: Function Layer](#layer-2-function-layer)
- [Layer 3: Mod Layer](#layer-3-mod-layer)
- [Available Macros](#available-macros)
- [Special Behaviors](#special-behaviors)

---

## Layer Overview

| Layer # | Name | Display Name | Purpose | Access Method |
|---------|------|--------------|---------|---------------|
| 0 | default_layer | Base | Custom Dvorak-inspired layout | Default active layer |
| 1 | keypad | Kp | Numpad functionality on right side | Toggle with top-left key or Layer 2 |
| 2 | fn | Fn | Function keys (F1-F12) | Hold MO(2) keys (bottom-left/right corners) |
| 3 | mod | Mod | System controls, Bluetooth, RGB, Backlight | Hold MO(3) key (top-right) |
| 4-7 | extra1-4 | Red/Purple/Cyan/Yellow | Reserved for future use | Not yet configured |

---

## Layer Access

### Layer Switching Keys
- **`tog 1`**: Toggle Layer 1 (Keypad) on/off
- **`mo 2`**: Momentary Layer 2 (Function) - active while held
- **`mo 3`**: Momentary Layer 3 (Mod) - active while held

---

## Layer 0: Base Layer

**Display Name:** Base
**Purpose:** Custom Dvorak-inspired layout with modifiers

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│   =    │ 1  │ 2  │ 3  │ 4  │ 5  │ TOG(1) │                                       │ MO(3)  │ 6  │ 7  │ 8  │ 9  │ 0  │   [   │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│  TAB   │ Q  │ P  │ U  │ Y  │ ;  │        │                                       │        │ K  │ F  │ L  │ R  │ B  │   \   │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│  ESC   │ A  │ O  │ E  │ I  │ G  │        │                                       │        │ D  │ H  │ T  │ N  │ S  │   -   │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ SHIFT  │ X  │ J  │ ,  │ =  │  '          │                                       │           C │ M  │ V  │ W  │ .  │ SHIFT │
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────┼────┼────┼────┼───────┴┐
  │MO(2) │ X  │ Z  │ ←  │ →                                                                          │ ↑  │ ↓  │ ]  │ \  │MO(2) │
  └──────┴────┴────┴────┘                                                                            └────┴────┴────┴───────┘

            Left Thumb Cluster                                                   Right Thumb Cluster
            ┌──────────────┐                                                     ┌──────────────┐
            │   LCTRL      │                                                     │   RCTRL      │
            ├──────────────┤                                                     ├──────────────┤
            │   LALT       │                                                     │              │
            ├──────────────┤                                                     ├──────────────┤
            │   LGUI       │                                                     │              │
            ├──────┬───────┤                                                     ├──────┬───────┤
            │ HOME │ PG_UP │                                                     │ END  │ PG_DN │
            ├──────┼───────┤                                                     ├──────┼───────┤
            │ BSPC │  DEL  │                                                     │ ENTER│ SPACE │
            └──────┴───────┘                                                     └──────┴───────┘
```

### Key Features:
- **Custom Dvorak-inspired layout** optimized for ergonomic typing
- Top row: Q-P-U-Y-; (left) | K-F-L-R-B (right)
- Home row vowels: A-O-E-I on left hand
- Home row consonants: D-H-T-N-S on right hand
- Bottom row: X-J-,-==' (left) | C-M-V-W-. (right)
- Full modifier keys (Ctrl, Alt, GUI/Win, Shift)
- Dedicated arrow keys
- Number row (1-0)
- Function layer access via MO(2) bottom corners
- Mod layer access via MO(3) top right
- Toggle Keypad layer via TOG(1) top left
- Custom control row with X and Z for quick access

---

## Layer 1: Keypad Layer

**Display Name:** Kp
**Purpose:** Numpad functionality on the right half

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────────┬──────────┬──────────┬──────────┬───────┐
│   =    │ 1  │ 2  │ 3  │ 4  │ 5  │ TRANS  │                                       │ MO(3)  │ 6  │ NUMLOCK│ KP_EQUAL │ KP_DIV   │ KP_MULT  │   -   │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────────┼──────────┼──────────┼──────────┼───────┤
│  TAB   │ Q  │ W  │ E  │ R  │ T  │        │                                       │        │ Y  │  KP_7  │   KP_8   │   KP_9   │ KP_MINUS │   \   │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────────┼──────────┼──────────┼──────────┼───────┤
│  ESC   │ A  │ S  │ D  │ F  │ G  │        │                                       │        │ H  │  KP_4  │   KP_5   │   KP_6   │ KP_PLUS  │   '   │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────────┼──────────┼──────────┼──────────┼───────┤
│ SHIFT  │ Z  │ X  │ C  │ V  │ B           │                                       │           N │  KP_1  │   KP_2   │   KP_3   │ KP_ENTER │ SHIFT │
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────────┼──────────┼──────────┼──────────┴───────┴┐
  │MO(2) │ `  │CAPS│ ←  │ →                                                                               │    ↑     │    ↓     │  KP_DOT  │    ]   │MO(2) │
  └──────┴────┴────┴────┘                                                                                 └──────────┴──────────┴──────────┴────────┘

            Left Thumb Cluster                                                   Right Thumb Cluster
            ┌──────────────┐                                                     ┌──────────────┐
            │   LCTRL      │                                                     │   RCTRL      │
            ├──────────────┤                                                     ├──────────────┤
            │   LALT       │                                                     │              │
            ├──────────────┤                                                     ├──────────────┤
            │   LGUI       │                                                     │              │
            ├──────┬───────┤                                                     ├──────┬───────┤
            │ HOME │ PG_UP │                                                     │ END  │ PG_DN │
            ├──────┼───────┤                                                     ├──────┼───────┤
            │ BSPC │  DEL  │                                                     │ ENTER│ KP_0  │
            └──────┴───────┘                                                     └──────┴───────┘
```

### Key Features:
- Full numpad on right half (7-8-9, 4-5-6, 1-2-3, 0)
- Numpad operators (/, *, -, +)
- Numpad Enter and Decimal point
- NumLock toggle
- Left half remains mostly same as Base layer
- Exit keypad mode using TRANS (transparent) or toggle again

---

## Layer 2: Function Layer

**Display Name:** Fn
**Purpose:** Function keys (F1-F12)

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│   F1   │ F2 │ F3 │ F4 │ F5 │ F6 │ TOG(1) │                                       │ MO(3)  │ F7 │ F8 │ F9 │ F10│ F11│  F12  │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│ TRANS  │    │    │    │    │    │        │                                       │        │    │    │    │    │    │       │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│ TRANS  │    │    │    │    │    │        │                                       │        │    │    │    │    │    │       │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ TRANS  │    │    │    │    │             │                                       │             │    │    │    │    │ TRANS │
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────┼────┼────┼────┼───────┴┐
  │TRANS │    │    │    │                                                                              │    │    │    │       │TRANS │
  └──────┴────┴────┴────┘                                                                              └────┴────┴────┴───────┘

            Left Thumb Cluster                                                   Right Thumb Cluster
            ┌──────────────┐                                                     ┌──────────────┐
            │   TRANS      │                                                     │   TRANS      │
            ├──────────────┤                                                     ├──────────────┤
            │   TRANS      │                                                     │              │
            ├──────────────┤                                                     ├──────────────┤
            │   TRANS      │                                                     │              │
            ├──────┬───────┤                                                     ├──────┬───────┤
            │ TRANS│ TRANS │                                                     │ TRANS│ TRANS │
            ├──────┼───────┤                                                     ├──────┼───────┤
            │ TRANS│ TRANS │                                                     │ TRANS│ TRANS │
            └──────┴───────┘                                                     └──────┴───────┘
```

### Key Features:
- Number row becomes F1-F12
- All other keys transparent (pass through to base layer)
- Can still toggle Keypad layer
- Can access Mod layer via MO(3)
- Accessed by holding MO(2) keys (bottom corners)

---

## Layer 3: Mod Layer

**Display Name:** Mod
**Purpose:** System controls, Bluetooth pairing, RGB/Backlight controls

```
┌──────────┬───────────┬───────────┬───────────┬───────────┬───────────┬──────┐                      ┌───────┬──────────┬──────────┬──────┬──────┬──────┬──────┐
│          │  BT_0     │  BT_1     │  BT_2     │  BT_3     │  BT_4     │      │                      │ TRANS │          │          │      │      │      │      │
├──────────┼───────────┼───────────┼───────────┼───────────┼───────────┼──────┤                      ├───────┼──────────┼──────────┼──────┼──────┼──────┼──────┤
│          │           │           │           │           │           │BOOTL │                      │ BOOTL │          │          │      │      │      │      │
├──────────┼───────────┼───────────┼───────────┼───────────┼───────────┤      │                      │       ├──────────┼──────────┼──────┼──────┼──────┼──────┤
│STUDIO_UNL│           │           │           │           │           │      │                      │       │STP_BAT   │          │      │      │      │      │
├──────────┼───────────┼───────────┼───────────┼───────────┼───────────┴──────┤                      ├───────┴──────────┼──────────┼──────┼──────┼──────┼──────┤
│          │           │           │           │ MACRO_VER │                   │                      │                  │          │      │      │      │      │
└─┬────────┼───────────┼───────────┼───────────┼───────────┴───────────────────┘                      └──────────────────┴──────────┼──────┼──────┼──────┼──────┴┐
  │        │           │           │           │                                                                                     │BL_INC│BL_DEC│      │      │      │
  └────────┴───────────┴───────────┴───────────┘                                                                                     └──────┴──────┴──────┴──────┘

            Left Thumb Cluster                                                   Right Thumb Cluster
            ┌──────────────┐                                                     ┌──────────────┐
            │              │                                                     │              │
            ├──────────────┤                                                     ├──────────────┤
            │              │                                                     │   BT_CLR     │
            ├──────────────┤                                                     ├──────────────┤
            │              │                                                     │              │
            ├──────┬───────┤                                                     ├──────┬───────┤
            │      │       │                                                     │      │       │
            ├──────┼───────┤                                                     ├──────┼───────┤
            │      │       │                                                     │BL_TOG│RGB_TOG│
            └──────┴───────┘                                                     └──────┴───────┘
```

### Key Features:

#### Bluetooth Controls:
- **BT_0 to BT_4**: Select Bluetooth profile (1-5)
- **BT_CLR**: Clear current Bluetooth profile (right thumb cluster)

#### System Controls:
- **BOOTLOADER**: Enter bootloader mode for firmware updates (both sides)
- **STUDIO_UNLOCK**: Unlock ZMK Studio (left ESC position)
- **MACRO_VER**: Display firmware version
- **STP_BAT**: Show battery status

#### Lighting Controls:
- **BL_TOG**: Toggle backlight on/off
- **BL_INC**: Increase backlight brightness (bottom right ↑)
- **BL_DEC**: Decrease backlight brightness (bottom right ↓)
- **RGB_TOG**: Toggle RGB underglow on/off

### Access:
Hold the MO(3) key (top right of keyboard) to access this layer.

---

## Available Macros

The firmware includes several useful macros defined in `config/macros.dtsi`:

### Programming Macros
| Macro Name | Output | Description |
|------------|--------|-------------|
| macro_quotes | `''` + ← | Auto-close single quotes |
| macro_dquotes | `""` + ← | Auto-close double quotes |
| macro_braces | `{}` + ← | Auto-close curly braces |
| macro_parens | `()` + ← | Auto-close parentheses |
| macro_brackets | `[]` + ← | Auto-close square brackets |

### Branding
| Macro Name | Output | Description |
|------------|--------|-------------|
| macro_kinesis | Kinesis | Types "Kinesis" |

### Windows Shortcuts
| Macro Name | Shortcut | Description |
|------------|----------|-------------|
| Win_Cut | Ctrl+X | Cut selection |
| Win_Copy | Ctrl+C | Copy selection |
| Win_Paste | Ctrl+V | Paste clipboard |
| Win_Select_All | Ctrl+A | Select all |
| Win_Undo | Ctrl+Z | Undo last action |
| Win_Desktop | Win+D | Show desktop |
| Win_File_Explorer | Win+E | Open File Explorer |
| Win_Snip_Tool | Win+Shift+S | Screenshot snip tool |
| Win_Show_All_Windows | Win+Tab | Task view |
| Win_Close_Program | Alt+F4 | Close program |
| Win_Settings_Menu | Win+I | Open Settings |
| Win_Lock_PC | Win+L | Lock PC |
| Win_Tile_Left | Win+← | Tile window left |
| Win_Tile_Up | Win+↑ | Maximize window |
| Win_Tile_Down | Win+↓ | Restore/Minimize |
| Win_Tile_Right | Win+→ | Tile window right |

### macOS Shortcuts
| Macro Name | Shortcut | Description |
|------------|----------|-------------|
| Mac_Cut | Cmd+X | Cut selection |
| Mac_Copy | Cmd+C | Copy selection |
| Mac_Paste | Cmd+V | Paste clipboard |
| Mac_Undo | Cmd+Z | Undo last action |
| Mac_Select_All | Cmd+A | Select all |
| Mac_Mission_Control | Ctrl+↑ | Show all windows |
| Mac_Snip_Tool | Cmd+Shift+Ctrl+4 | Screenshot tool |
| Mac_Close_Program | Cmd+Q | Quit application |
| Mac_Spotlight_Search | Cmd+Space | Spotlight search |
| Mac_Strike_Through_Text | Cmd+Shift+X | Strikethrough text |

### Mouse Macros
| Macro Name | Action | Description |
|------------|--------|-------------|
| Double_Click | Click×2 | Double mouse click |

---

## Special Behaviors

### Homerow Mods
The firmware includes a `homerow_mods` behavior configured with:
- **Tapping term**: 200ms
- **Quick tap**: 175ms
- **Flavor**: tap-preferred
- Currently not actively used in the default keymap but available for customization

### Layer Status Display
Each layer has a display name shown on the keyboard's status display:
- Layer 0: **Base**
- Layer 1: **Kp** (Keypad)
- Layer 2: **Fn** (Function)
- Layer 3: **Mod** (Modifier)
- Layer 4: **Red** (Reserved)
- Layer 5: **Purple** (Reserved)
- Layer 6: **Cyan** (Reserved)
- Layer 7: **Yellow** (Reserved)

---

## Quick Reference

### Common Key Abbreviations
| Code | Key | Code | Key |
|------|-----|------|-----|
| LCTRL | Left Control | RCTRL | Right Control |
| LALT | Left Alt | RGUI | Right GUI/Win |
| LSHFT | Left Shift | RSHFT | Right Shift |
| BSPC | Backspace | DEL | Delete |
| ESC | Escape | TAB | Tab |
| CAPS | Caps Lock | ENTER | Enter/Return |
| PG_UP | Page Up | PG_DN | Page Down |
| TRANS | Transparent (pass-through) | MO(n) | Momentary layer n |
| TOG(n) | Toggle layer n | BOOTL | Bootloader mode |

---

## Configuration Files

- **Main Keymap**: `config/adv360.keymap`
- **Macros**: `config/macros.dtsi`
- **Version Info**: `config/version.dtsi`
- **Keyboard Info**: `config/info.json`

---

*Generated from ZMK firmware configuration for Kinesis Adv360 Pro*
