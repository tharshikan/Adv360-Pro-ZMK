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
| 1 | sym_numpad | Sym+Num | Symbols/brackets on left, numpad on right | **Sticky Layer** - Press top-left key (SL 1) |
| 2 | fn | Fn | Function keys (F1-F12) | Hold MO(2) keys (bottom-left/right corners) |
| 3 | mod | Mod | System controls, Bluetooth, RGB, Backlight | Hold MO(3) key (top-right) |
| 4-7 | extra1-4 | Red/Purple/Cyan/Yellow | Reserved for future use | Not yet configured |

---

## Layer Access

### Layer Switching Keys
- **`sl 1`**: Sticky Layer 1 (Symbols+Numpad) - activates for next keypress only
  - Available in **two locations**: Top-left corner AND right home row (after S key)
- **`mo 2`**: Momentary Layer 2 (Function) - active while held
- **`mo 3`**: Momentary Layer 3 (Mod) - active while held

### What is a Sticky Layer?
A **sticky layer** activates temporarily for just the **next keypress**, then automatically returns to the base layer. This is perfect for typing a single symbol or number without staying in that layer.

**How it works:**
1. Press `SL 1` (top-left key)
2. Layer 1 activates and waits
3. Press any key (e.g., `(` or `7`)
4. That key is sent, then automatically returns to base layer

**Example usage:**
- Need a `(`? Press SL 1, then press the `(` key → Returns to base
- Need number 7? Press SL 1, then press `7` → Returns to base
- Want multiple symbols? Press SL 1 before each one

**Benefits over toggle:**
- ✅ No need to remember to turn layer off
- ✅ Faster for single symbols/numbers
- ✅ Prevents accidentally staying in wrong layer
- ✅ More efficient workflow for occasional symbol use

---

## Layer 0: Base Layer

**Display Name:** Base
**Purpose:** Custom Dvorak-inspired layout with modifiers

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│   =    │ 1  │ 2  │ 3  │ 4  │ 5  │ SL(1)  │                                       │ MO(3)  │ 6  │ 7  │ 8  │ 9  │ 0  │   [   │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│  TAB   │ Q  │ P  │ U  │ Y  │ ;  │        │                                       │        │ K  │ F  │ L  │ R  │ B  │   \   │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│  ESC   │ A  │ O  │ E  │ I  │ G  │        │                                       │        │ D  │ H  │ T  │ N  │ S  │ SL(1) │
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
            ├──────┼───────┤                                                     ├──────┬───────┤
            │ BSPC │  CMD  │                                                     │ENTER │ SPACE │
            │      │ (GUI) │                                                     │CMD^  │       │
            └──────┴───────┘                                                     └──────┴───────┘
                                                                                  ^ Tap=Enter, Hold=CMD
```

### Key Features:
- **Custom Dvorak-inspired layout** optimized for ergonomic typing
- Top row: Q-P-U-Y-; (left) | K-F-L-R-B (right)
- Home row vowels: A-O-E-I on left hand
- Home row consonants: D-H-T-N-S on right hand
- Bottom row: X-J-,-==' (left) | C-M-W-V-. (right)
- **Thumb cluster with Command + Shift access:**
  - **Left thumb:** Backspace (tap) / Left Shift (hold) plus dedicated Command/GUI key
  - **Right thumb:** Enter (tap) / Command (hold) plus Space (tap) / Right Shift (hold)
  - Dual-role thumbs keep both Shift modifiers close without sacrificing Command reach
  - **Right Command + D/H/T/N:** Hold the right Command (Enter) key with D/H/T/N to send ← ↓ ↑ → for Vim-style navigation without leaving home row
  - Enter key doubles as Command when held for shortcuts
- Full modifier keys also available on upper thumb cluster (Ctrl, Alt, GUI)
- Dedicated arrow keys
- Number row (1-0)
- Function layer access via MO(2) bottom corners
- Mod layer access via MO(3) top right
- **Sticky Layer access in TWO locations:**
  - **SL(1) top left** - easy reach with left hand
  - **SL(1) right home row** - replaces minus key, ergonomic pinky access
- Custom control row with X and Z for quick access

### Thumb Cluster Command & Shift Keys:
The bottom thumb keys now cover both GUI and Shift modifiers without leaving home row:

- **Backspace ↔ Left Shift (`bs_shift`):**
  - **Tap:** Sends Backspace on every layer
  - **Hold:** Acts as Left Shift using a forgiving 240 ms tapping term so you can roll into modifiers without misfires

- **Dedicated Command key:**
  - Left inner thumb key remains a plain Command/GUI key for combo-heavy workflows

- **Enter ↔ Command (`enter_cmd`):**
  - **Tap:** Enter
  - **Hold:** Command/GUI (tap-preferred, 200 ms)

- **Space (or KP_0) ↔ Right Shift (`sp_shift`):**
  - **Tap:** Space on the base layer, KP_0 on Sym+Num
  - **Hold:** Acts as Right Shift with a snappy 200 ms tapping term for quick rolls

Because `bs_shift` and `sp_shift` are dedicated behaviors, the Shift hold works even after layer switches—perfect for typing symbols or numbers while still getting uppercase characters.

- **Vim-style navigation chord:**
  - Hold the right Command (Enter) key and tap **D / H / T / N** to send **← / ↓ / ↑ / →** respectively
  - Gives you instant home-row navigation when you temporarily need arrow keys

**Example usage:**
- Hold Backspace and tap a letter to capitalize it without moving pinkies
- Hold Space while pressing arrow keys to select text (acts like Shift+Arrow)
- Tap Enter normally; hold Enter then tap a key for Cmd/Win shortcuts
- Cmd+Space (Spotlight) still works: hold Enter (Command) + tap the Space/Shift key

### Home Row Mods Status:
⚠️ **Currently Disabled** - Home row modifiers are defined in the firmware but not active on the base layer. The home row keys (A, O, E, I, H, T, N, S) currently function as regular letters only.

To enable home row mods, you would need to replace the home row `&kp` bindings with `&hml` (left) and `&hmr` (right) behaviors in the keymap file. See the detailed configuration below for instructions.

### Home Row Mods Explained (Available But Not Active):
The home row modifiers are fully defined and ready to use. When enabled, the home row keys would double as modifiers when held, allowing you to keep your fingers on the home row while accessing all modifier combinations. This implementation uses **bilateral combinations** (positional hold-taps) which means:
- Left-hand mods (A, O, E, I) only activate when you press a **right-hand** key while holding them
- Right-hand mods (H, T, N, S) only activate when you press a **left-hand** key while holding them
- This prevents accidental modifier activation when typing same-hand combinations like "as" or "in"
- The "balanced" flavor and hold-trigger-on-release setting provide the most reliable behavior

#### Home Row Mods Visual Reference:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        HOME ROW MODIFIERS                               │
│                     (Bilateral Combinations)                            │
└─────────────────────────────────────────────────────────────────────────┘

         LEFT HAND                                    RIGHT HAND
    ┌─────────────────┐                          ┌─────────────────┐
    │  Pinky  Ring Mid│ Index                Index│ Mid  Ring Pinky │
    └─────────────────┘                          └─────────────────┘

         TAP (Normal):
    ┌─────┬─────┬─────┬─────┬─────┐        ┌─────┬─────┬─────┬─────┬─────┐
    │  A  │  O  │  E  │  I  │  G  │        │  D  │  H  │  T  │  N  │  S  │
    └─────┴─────┴─────┴─────┴─────┘        └─────┴─────┴─────┴─────┴─────┘

         HOLD (Modifier):
    ┌─────┬─────┬─────┬─────┬─────┐        ┌─────┬─────┬─────┬─────┬─────┐
    │SHIFT│CTRL │ ALT │ GUI │  G  │        │  D  │ GUI │ ALT │CTRL │SHIFT│
    └─────┴─────┴─────┴─────┴─────┘        └─────┴─────┴─────┴─────┴─────┘
       ▲     ▲     ▲     ▲                            ▲     ▲     ▲     ▲
       │     │     │     │                            │     │     │     │
       └─────┴─────┴─────┴────────────────────────────┴─────┴─────┴─────┘
                    Only work with opposite hand!

┌─────────────────────────────────────────────────────────────────────────┐
│  ACTIVATION RULES:                                                      │
│                                                                          │
│  ✓ Left mods (A/O/E/I) + Right keys → Modifier activates               │
│  ✓ Right mods (H/T/N/S) + Left keys → Modifier activates               │
│  ✗ Same-hand combinations → No modifier (normal typing)                │
│                                                                          │
│  Examples:                                                              │
│  • Hold O (Ctrl) + Press K (right) = Ctrl+K         ✓                  │
│  • Hold T (Alt) + Press Q (left) = Alt+Q            ✓                  │
│  • Hold A (Shift) + Press L (right) = Capital L     ✓                  │
│  • Type "oil" fast = o-i-l (no mods triggered)      ✓                  │
│  • Type "as" fast = a-s (no mods triggered)         ✓                  │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│  COMMON SHORTCUTS:                                                      │
│                                                                          │
│  Left Hand Mods:                     Right Hand Mods:                   │
│  • A+Click → Shift+Click             • H+Q → Cmd/Win+Q                  │
│  • O+K → Ctrl+K                      • T+Tab → Alt+Tab                  │
│  • E+F → Alt+F                       • N+W → Ctrl+W                     │
│  • I+Space → Cmd/Win+Space           • S+Click → Shift+Click            │
│                                                                          │
│  Multi-Mod Combinations:                                                │
│  • Hold O+I → Ctrl+Cmd (both left)                                     │
│  • Then press right key for combo: Ctrl+Cmd+K                          │
│  • Hold T+N → Alt+Ctrl (both right)                                    │
│  • Then press left key for combo: Alt+Ctrl+Q                           │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Quick Reference Table:

| Finger | Left Hand | Modifier | Right Hand | Modifier |
|--------|-----------|----------|------------|----------|
| Pinky  | A         | Shift    | S          | Shift    |
| Ring   | O         | Ctrl     | N          | Ctrl     |
| Middle | E         | Alt      | T          | Alt      |
| Index  | I         | GUI/Cmd  | H          | GUI/Cmd  |
| Index  | G         | (none)   | D          | (none)   |

**Example usage (when enabled):**
- Hold **O** (Ctrl) + press **K** (right hand) = Ctrl+K
- Hold **T** (Alt) + press **Q** (left hand) = Alt+Q
- Hold **A** (Shift) + press **L** (right hand) = Shift+L (capital L)
- Typing "oil" normally works fine because O-I-L doesn't trigger mods (no cross-hand combo)

#### How to Enable Home Row Mods:
To activate home row modifiers, edit `config/adv360.keymap` line 50 and replace:
```
&kp ESC    &kp A      &kp O     &kp E        &kp I         &kp G      &none     &kp LCTRL  &kp LALT      &kp LGUI   &kp RCTRL    &none          &kp D      &kp H       &kp T       &kp N       &kp S       &kp MINUS
```

With:
```
&kp ESC    &hml LSHFT A    &hml LCTRL O   &hml LALT E  &hml LGUI I   &kp G      &none     &kp LCTRL  &kp LALT      &kp LGUI   &kp RCTRL    &none          &kp D      &hmr RGUI H    &hmr RALT T   &hmr RCTRL N &hmr RSHFT S    &kp MINUS
```

This changes:
- **A** → Shift when held (left)
- **O** → Ctrl when held (left)
- **E** → Alt when held (left)
- **I** → GUI/Cmd when held (left)
- **H** → GUI/Cmd when held (right)
- **T** → Alt when held (right)
- **N** → Ctrl when held (right)
- **S** → Shift when held (right)

---

## Layer 1: Symbols + Numpad Layer

**Display Name:** Sym+Num
**Purpose:** Programming symbols and brackets on left, numpad on right

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────────┬──────────┬──────────┬──────────┬───────┐
│   =    │ 1  │ 2  │ 3  │ 4  │ 5  │  ---   │                                       │ MO(3)  │ 6  │ NUMLOCK│ KP_EQUAL │ KP_DIV   │ KP_MULT  │   -   │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────────┼──────────┼──────────┼──────────┼───────┤
│  TAB   │  ) │  } │ -  │ ]  │ ]  │        │                                       │        │ Y  │  KP_7  │   KP_8   │   KP_9   │ KP_MINUS │   \   │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────────┼──────────┼──────────┼──────────┼───────┤
│  ESC   │ (  │ {  │ _  │ [  │    │        │                                       │        │ H  │  KP_4  │   KP_5   │   KP_6   │ KP_PLUS  │   '   │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────────┼──────────┼──────────┼──────────┼───────┤
│ SHIFT  │ Z  │    │ `  │ ~  │             │                                       │           N │  KP_1  │   KP_2   │   KP_3   │ KP_ENTER │ SHIFT │
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

#### Left Hand - Programming Symbols:
- **Brackets & Parentheses:**
  - Top row: `)` `}` `-` `]` `]`
  - Home row: `(` `{` `_` `[`
- **Special Characters:**
  - Bottom row: `` ` `` `~`
- **Perfect for coding:** All common bracket pairs easily accessible
- **Symmetric placement:** Opening brackets on home row, closing on top row

#### Right Hand - Full Numpad:
- Calculator-style layout: 7-8-9, 4-5-6, 1-2-3, 0
- Numpad operators: `/` `*` `-` `+`
- Numpad Enter for quick calculations
- Decimal point (`.`) for numbers
- NumLock toggle for compatibility

#### Usage:
- **Sticky Layer Access:** Press SL(1) top-left key from base layer
- **One key at a time:** Layer activates for next keypress only, then returns to base
- **Perfect for single symbols:** Press SL(1), type `(`, automatically back to base
- **Perfect for single numbers:** Press SL(1), type `7`, automatically back to base
- **Multiple symbols:** Press SL(1) before each symbol you need
- **No toggle-off needed:** Automatically returns to base layer after each keypress
- **Dual purpose:** Code symbols on left, numpad on right
- **Efficient workflow:** Quick access to any bracket or number without staying in the layer

#### Thumb Behavior:
- **Backspace ↔ Left Shift:** Same `bs_shift` behavior from the base layer lives here, so you can hold the left thumb key to Shift while still tapping brackets or symbols.
- **Space/KP_0 ↔ Right Shift:** `sp_shift` now taps `KP_0` for the numpad but still provides Right Shift on hold for typing `)`/`}` or doing Shift+Numpad combos.

---

## Layer 2: Function Layer

**Display Name:** Fn
**Purpose:** Function keys (F1-F12)

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│   F1   │ F2 │ F3 │ F4 │ F5 │ F6 │ SL(1)  │                                       │ MO(3)  │ F7 │ F8 │ F9 │ F10│ F11│  F12  │
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
- **Can activate Sticky Layer** via SL(1) for one symbol/number
- Can access Mod layer via MO(3)
- Accessed by holding MO(2) keys (bottom corners)
- Perfect for Function key shortcuts while having quick symbol access

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

### Sticky Layer (Symbols + Numpad)

**Status:** ✅ Active - **Two locations** for easy access

Layer 1 (Symbols + Numpad) uses a **sticky layer** activation instead of a toggle. This means the layer activates for exactly one keypress, then automatically returns to the previous layer.

**Two activation keys available:**
1. **Top-left corner** (= position): Easy reach for left hand
2. **Right home row** (after S key, pinky): Ergonomic home-row access

Both keys do the same thing - activate Layer 1 for one keypress. Use whichever is more convenient!

**Benefits:**
- **No mental overhead:** Don't need to remember to turn layer off
- **Faster workflow:** Press SL(1), type symbol, already back to base
- **Prevents errors:** Can't accidentally stay stuck in wrong layer
- **Perfect for coding:** Quick access to brackets without layer management
- **Efficient for numbers:** Type single digits from numpad without commitment

**How to use:**
1. Press `SL 1` - either:
   - Top-left key (= position) with left hand, or
   - Right home row (right pinky) after S key
2. The layer indicator shows Sym+Num is active
3. Press any key (e.g., `(`, `7`, `}`)
4. Automatically returns to base layer
5. Repeat as needed for each symbol/number

**Which key to use?**
- **Top-left (left hand):** Use when typing with right hand or need top-row reach
- **Right home row (right pinky):** Most ergonomic - no hand movement from home position
  - ✅ **Recommended for frequent use** - keeps fingers on home row
  - ✅ Perfect for coding workflows - type letter, hit SL with pinky, type bracket, continue
  - ✅ Replaces minus key (which is now available on Layer 1 anyway)
- **Personal preference:** Try both and use whichever feels better for your workflow

**Why two locations?**
Having sticky layer access in two spots gives you flexibility:
- Use **top-left** when your right hand is on the mouse
- Use **home row** when actively typing (most efficient)
- Both activate the same layer - no difference in functionality
- **Ergonomic advantage:** Home row access means zero hand movement for layer switching

**Comparison with other layer types:**
- **Toggle (`tog`):** Press once to turn on, press again to turn off - can forget and stay in layer
- **Momentary (`mo`):** Active only while held - requires holding key down
- **Sticky (`sl`):** Active for next keypress only - best of both worlds ✓

**Practical examples:**
```
Typing: if (condition) {
1. Type: if
2. Press SL(1), press ( → if (
3. Type: condition
4. Press SL(1), press ) → if (condition)
5. Type: space
6. Press SL(1), press { → if (condition) {
```

```
Entering a number: Item #7
1. Type: Item #
2. Press SL(1), press 7 → Item #7
```

```
Multiple brackets in sequence:
1. Press SL(1), press ( → (
2. Press SL(1), press { → ({
3. Press SL(1), press [ → ({[
4. Type code...
5. Press SL(1), press ] → ({[...]
6. Press SL(1), press } → ({[...]}
7. Press SL(1), press ) → ({[...]})
```

---

### Enter/Command Dual-Function Key

**Status:** ✅ Active on base layer (right thumb Enter key)

The Enter key on the right thumb doubles as a Command/GUI modifier when held:

**Configuration (`enter_cmd`):**
- **Tapping term:** 200ms
- **Quick tap:** 175ms
- **Flavor:** tap-preferred (prioritizes tap/Enter for normal typing)
- **Behavior:** Tap = Enter, Hold = Command/GUI

**How it works:**
- Quick press and release → Enter key (normal line breaks)
- Press and hold while tapping another key → Command modifier
- The "tap-preferred" flavor ensures you get Enter even if you're slightly slow to release

**Perfect for:**
- Normal typing: Quick taps send Enter as expected
- Shortcuts: Hold for Cmd+Enter, Cmd+K, etc.
- One-handed shortcuts: Hold Enter (right thumb) + press keys with left hand

---

### Timeless Home Row Modifiers (Bilateral Combinations)

⚠️ **Status: Defined but not currently active on base layer**

The firmware has advanced home row modifiers fully configured using **bilateral combinations** (positional hold-taps) for maximum reliability. The behaviors are ready to use but not currently applied to the home row keys:

#### Left Hand Home Row Mods (`hml`)
- **Keys**: A (Shift), O (Ctrl), E (Alt), I (GUI/Cmd)
- **Configuration**:
  - Tapping term: 280ms
  - Quick tap: 175ms
  - Prior idle requirement: 125ms
  - Flavor: balanced
  - Hold-trigger positions: Right hand keys only (38-74)
  - Hold-trigger-on-release: enabled
- **Behavior**: These mods only activate when you press a right-hand key while holding them

#### Right Hand Home Row Mods (`hmr`)
- **Keys**: H (GUI/Cmd), T (Alt), N (Ctrl), S (Shift)
- **Configuration**:
  - Tapping term: 280ms
  - Quick tap: 175ms
  - Prior idle requirement: 125ms
  - Flavor: balanced
  - Hold-trigger positions: Left hand keys only (0-37)
  - Hold-trigger-on-release: enabled
- **Behavior**: These mods only activate when you press a left-hand key while holding them

#### Why Bilateral Combinations?
This approach prevents accidental modifier activation when:
- Typing fast same-hand combinations (e.g., "as", "in", "the")
- Rolling fingers on the same hand
- Performing common typing patterns

The "balanced" flavor provides optimal behavior by:
- Preferring hold if you're slow to release
- Preferring tap if you quickly move to the next key
- Using hold-trigger-on-release to wait until key release before deciding

#### Adjustment Tips
If you experience issues:
- **Too many misfires**: Increase `tapping-term-ms` (try 300-320ms)
- **Mods too slow to activate**: Decrease `require-prior-idle-ms` (try 100ms)
- **Trouble with rolling**: Increase `quick-tap-ms` (try 200ms)

### Layer Status Display
Each layer has a display name shown on the keyboard's status display:
- Layer 0: **Base**
- Layer 1: **Sym+Num** (Symbols + Numpad)
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
| SL(n) | Sticky layer n (one keypress) | BOOTL | Bootloader mode |

---

## Configuration Files

- **Main Keymap**: `config/adv360.keymap`
- **Macros**: `config/macros.dtsi`
- **Version Info**: `config/version.dtsi`
- **Keyboard Info**: `config/info.json`

---

*Generated from ZMK firmware configuration for Kinesis Adv360 Pro*
