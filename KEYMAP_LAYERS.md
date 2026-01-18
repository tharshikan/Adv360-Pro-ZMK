# Kinesis Adv360 Pro - Keymap Layers Documentation

This document provides a comprehensive visual reference for all keyboard layers configured in this ZMK firmware.

## Table of Contents
- [Layer Overview](#layer-overview)
- [Layer Access](#layer-access)
- [Layer 0: Base Layer](#layer-0-base-layer)
- [Layer 1: Keypad Layer](#layer-1-keypad-layer)
- [Layer 2: Function Layer](#layer-2-function-layer)
- [Layer 3: Mod Layer](#layer-3-mod-layer)
- [Layer 4: Nav Layer](#layer-4-nav-layer)
- [Special Behaviors](#special-behaviors)

---

## Layer Overview

| Layer # | Name | Display Name | Purpose | Access Method |
|---------|------|--------------|---------|---------------|
| 0 | default_layer | Base | Custom Dvorak-inspired layout | Default active layer |
| 1 | sym_numpad | Sym+Num | Symbols/brackets on left, numpad on right | **Sticky Layer** (Tap SL) or **Smart Toggle** (Double-Tap PG_DN) |
| 2 | fn | Fn | Function keys (F1-F12) | Hold MO(2) keys (bottom-left/right corners) |
| 3 | mod | Mod | System controls, Bluetooth, RGB, Backlight | Hold MO(3) key (top-right) |
| 4 | nav | Nav | Navigation Arrows & Copy/Paste shortcuts | **Hold either Command (Thumb)** |

---

## Layer Access

### Layer Switching Keys
- **`sl 1`**: Sticky Layer 1 (Symbols+Numpad) - activates for next keypress only.
- **`td_sym` (Smart Toggle)**: Replaces Page Down on the right thumb.
  - **Tap**: Acts as `sl 1` (Sticky Layer).
  - **Double Tap**: Toggles Layer 1 ON/OFF.
- **`nav` (Hold)**: Hold either Command/Enter thumb key to access arrows and shortcuts.

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
            │   NAV (Hold) │                                                     │              │
            ├──────┬───────┤                                                     ├──────┬───────┤
            │ HOME │ PG_UP │                                                     │ END  │ TD(1)^│
            ├──────┼───────┤                                                     ├──────┬───────┤
            │ BSPC │  NAV  │                                                     │ NAV  │ SPACE │
            │      │ (Hold)│                                                     │(Hold)│       │
            └──────┴───────┘                                                     └──────┴───────┘
                                                                               ^ Smart Toggle: Tap=Stick, Dbl=Tog
```

### Key Features:
- **Navigation Layer (NAV):** Hold either Command thumb key (Left inner or Right inner/Enter) to access arrows and shortcuts.
- **Smart Toggle (TD 1):** The Page Down key (right thumb) creates a smart layer toggle:
  - **Tap:** Activates Sym layer for ONE keypress (Sticky).
  - **Double Tap:** Toggles Sym layer ON until you double-tap again.
- **Dvorak-inspired Layout:** A-O-E-I (left home) and D-H-T-N-S (right home).
- **Dual-role Thumbs:**
  - **Left Outer:** Backspace (Tap) / Shift (Hold)
  - **Right Outer:** Space (Tap) / Shift (Hold)

---

## Layer 1: Symbols + Numpad Layer

**Display Name:** Sym+Num
**Purpose:** Programming symbols and brackets on left, numpad on right

*Same layout as standard, accessed via Smart Toggle.*

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────────┬──────────┬──────────┬──────────┬───────┐
│   =    │ 1  │ 2  │ 3  │ 4  │ 5  │  ---   │                                       │ MO(3)  │ ^  │ NUMLOCK│ KP_EQUAL │ KP_DIV   │ KP_MULT  │   -   │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────────┼──────────┼──────────┼──────────┼───────┤
│  TAB   │  ] │  } │ -  │ )  │ /  │        │                                       │        │ @  │  KP_7  │   KP_8   │   KP_9   │ KP_MINUS │   \   │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────────┼──────────┼──────────┼──────────┼───────┤
│  ESC   │  [ │  { │ _  │ (  │ \  │        │                                       │        │ #  │  KP_4  │   KP_5   │   KP_6   │ KP_PLUS  │   '   │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────────┼──────────┼──────────┼──────────┼───────┤
│ SHIFT  │ !  │ $  │ %  │ ^  │ ~           │                                       │           : │  KP_1  │   KP_2   │   KP_3   │ KP_ENTER │ SHIFT │
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────────┼──────────┼──────────┼──────────┴───────┴┐
  │MO(2) │ /  │ \  │ |  │ →                                                                               │    ↑     │    ↓     │  KP_DOT  │    ]   │MO(2) │
  └──────┴────┴────┴────┘                                                                                 └──────────┴──────────┴──────────┴────────┘
```

---

## Layer 4: Nav Layer

**Display Name:** Nav
**Purpose:** Navigation Arrows, Shortcuts (Copy/Paste), and Command Modifiers
**Access:** **Hold** Left Command or Right Command/Enter (Thumb Keys)

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│ CMD+1  │CMD1│CMD2│CMD3│CMD4│CMD5│        │                                       │        │CMD6│CMD7│CMD8│CMD9│CMD0│ CMD+[ │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│ CMD+Tab│CMDQ│CMDP│CMDU│CMDY│CMD;│        │                                       │        │CMDK│CMDF│CMDL│CMDR│CMDB│ CMD+\ │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│ CMD+Esc│CMDA│CMDO│CMDE│CMDI│CMDG│        │                                       │        │ ←  │ ↓  │ ↑  │ →  │CMDS│       │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ CMD+Sft│Undo│Cut │Copy│Pste│CMD'         │                                       │             │CMDC│CMDM│CMDW│CMDV│CMD. │ CMD+Sft│
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────┼────┼────┼────┼───────┴┐
  │      │CMDX│CMDZ│CMD←│CMD→                                                                         │CMD↑│CMD↓│CMD]│CMD\│      │
  └──────┴────┴────┴────┘                                                                             └────┴────┴────┴───────┘
```

### Key Features:

#### 1. Universal Command Modifier
- **All keys** (except navigation arrows) act as `Command + Key`.
- This allows you to hold the Nav thumb key and perform any shortcut (e.g., `Cmd+S` to save, `Cmd+Tab` to switch apps).
- Works with **either hand** (Nav layer uses Left Command regardless of which thumb activates it).

#### 2. Arrow Keys (Right Hand Home Row)
- **D**: Left Arrow
- **H**: Down Arrow
- **T**: Up Arrow
- **N**: Right Arrow
- **Why?** Keeps your hand on the home row while navigating.

#### 3. One-Handed Copy/Paste (Left Hand Row 4)
Ergonomic shortcuts placed on the row above the thumbs (mimicking Z/X/C/V positions):
- **Pinky (Z key pos)**: **Undo** (`Cmd+Z`)
- **Ring (X key pos)**: **Cut** (`Cmd+X`)
- **Middle (C key pos)**: **Copy** (`Cmd+C`)
- **Index (V key pos)**: **Paste** (`Cmd+V`)

---

## Special Behaviors

### Smart Layer Toggle (`td_sym`)
The **Page Down** key on the right thumb has been upgraded to a **Tap Dance** key:
- **Tap**: Acts as a **Sticky Layer** (`sl 1`). Press it once, then press your symbol/number key. The layer deactivates immediately after.
- **Double Tap**: Acts as a **Layer Toggle** (`tog 1`). Locks the Symbols layer ON. Double-tap again to turn it OFF.

### Thumb Modifiers
- **Left Thumb (Inner)**: Hold for **Nav Layer** (Command).
- **Right Thumb (Inner)**: Tap for **Enter**, Hold for **Nav Layer** (Command).
- **Left Thumb (Outer)**: Tap for **Backspace**, Hold for **Shift**.
- **Right Thumb (Outer)**: Tap for **Space**, Hold for **Shift**.

---
*Generated from ZMK firmware configuration for Kinesis Adv360 Pro*
