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
- [Layer 5: Cursor Layer](#layer-5-cursor-layer)
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
| 5 | cursor | Cursor | VIM arrows, text selection, find operations | **Hold bottom-right corner key** |

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
  │MO(2) │ X  │ Z  │ ←  │ →                                                                          │ ↑  │ ↓  │ ]  │MO(5)│MO(2) │
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
- **Cursor Layer:** Hold the **bottom-right corner key** (MO(5), second from right) to access VIM arrows, text selection, and find operations. See [Layer 5: Cursor Layer](#layer-5-cursor-layer) for details.
- **Smart Toggle (TD 1):** The Page Down key (right thumb) creates a smart layer toggle:
  - **Tap:** Activates Sym layer for ONE keypress (Sticky).
  - **Double Tap:** Toggles Sym layer ON until you double-tap again.
- **Dvorak-inspired Layout:** A-O-E-I (left home) and D-H-T-N-S (right home).
- **Dual-role Thumbs:**
  - **Left Outer:** Backspace (Tap) / Shift (Hold)
  - **Right Outer:** Space (Tap) / Shift (Hold)
- **Note:** Backslash (\\) is still accessible via Symbol Layer (Layer 1), as the bottom-right corner key now activates the Cursor layer.

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
  │MO(2) │ `  │ *  │ |  │ :                                                                               │    ↑     │    ↓     │  KP_DOT  │    ]   │MO(2) │
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

## Layer 5: Cursor Layer

**Display Name:** Cursor
**Purpose:** Advanced text editing with VIM-style arrows, text selection macros, find operations, and one-handed editing
**Access:** **Toggle** via the **Page Up** key on the inner thumb cluster (Base Layer)

```
┌────────┬────────┬────────┬────────┬────────┬────────┬────────┐                                       ┌────────┬──────┬──────┬──────┬──────┬───────┬───────┐
│  ESC   │ Enter  │ Space  │  Tab   │  BSPC  │  INS   │ WinTab │                                       │ AltTab │ INS  │ DEL  │ Tab  │ Space │ Enter │  ESC  │
├────────┼────────┼────────┼────────┼────────┼────────┼────────┤                                       ├────────┼──────┼──────┼──────┼───────┼───────┼───────┤
│ Search │ Sft(S) │  Redo  │  Undo  │  BSPC  │  Cut   │ WinMsn │                                       │        │ Cut  │ BSPC │ Undo │ Redo  │ Sft(S)│ Search│
├────────┼────────┼────────┼────────┼────────┼────────┤ Ctrl   │                                       │  Tab   ├──────┼──────┼──────┼───────┼───────┼───────┤
│ URLBar │  Win   │  Alt   │  Ctrl  │ Shift  │  Copy  │ Tab    │                                       │        │ Copy │  ←   │  ↑   │  ↓    │   →   │ URLBar│
├────────┼────────┼────────┼────────┼────────┼────────┴────────┤                                       ├────────┴──────┼──────┼──────┼───────┼───────┼───────┤
│ DwnLd  │ SelAll │ SelLn  │ SelWd  │  Find  │ Paste           │                                       │ Paste         │ Home │ PgUp │ PgDn  │  End  │ DwnLd │
└─┬──────┼────────┼────────┼────────┼────────┴─────────────────┘                                       └───────────────┴──────┼──────┼───────┴───────┴───────┘
  │FindRep│FindPrv│ ExtLn  │ ExtWd  │ FindNxt                                                                 FindNxt │ ExtWd│ ExtLn│FindPrv│FindRep│
  └───────┴───────┴────────┴────────┴───────┘      ┌───────┐┌───────┐┌──────┐   ┌───────┐┌───────┐┌──────┐    └───────┴──────┴──────┴───────┴───────┘
                                                   │UnlckL5││  Tab  ││CtrlTb│   │SelNone││ExtLine││ExtWrd│
                                                   └───────┘└───────┘└──────┘   └───────┘└───────┘└──────┘

            Legend:
            Search   = Spotlight Search (Cmd+Space)
            URLBar   = Focus URL Bar (Cmd+L)
            DwnLd    = Downloads (Cmd+Opt+L)
            FindRep  = Find & Replace (Cmd+Opt+F)
            WinTab   = Mission Control (Ctrl+Up)
            AltTab   = App Switcher (Cmd+Tab) / CtrlTab = Tab Switcher
            Sft(S)   = Sticky Shift
            SelLn/Wd = Select Line/Word (Thumb/Keys)
            ExtLn/Wd = Extend Line/Word (Thumb/Keys)
            SelAll   = Select All (Cmd+A)
            Find     = Cmd+F (Find)
            FindNxt  = Find Next (Cmd+G) / FindPrv = Find Prev (Cmd+Shift+G)
```

### Key Features:

#### 1. Fully Integrated Editing Environment
The new Cursor Layer is a complete command center for text editing and navigation, inspired by Sunaku's Glove80 layout.
- **Top Rows**: Common keys (Esc, Enter, Space, Tab) mirrored on both sides for easy access.
- **Home Row**: Modifiers (Left) and Arrows (Right) for "home row computing".
- **Inner Columns**: Editing stack (Cut, Copy, Paste) available to both index fingers.
- **Outer Columns**: App navigation (Search, URL Bar, Downloads).

#### 2. VIM-Style Arrow Keys (Right Home Row)
- **H position**: **←** Left Arrow
- **J position**: **↑** Up Arrow
- **K position**: **↓** Down Arrow
- **L position**: **→** Right Arrow
*(Note: Mapped to physical Dvorak positions H, T, N, S)*

#### 3. Smart Macros
- **Search Bar**: Quickly open Spotlight/App Launcher.
- **URL Bar**: Instantly focus browser address bar.
- **Downloads**: Open downloads folder/tab.
- **Find & Replace**: Trigger advanced find.
- **Window Management**: Mission Control (WinTab) and App Switcher (AltTab) on left thumb.

#### 4. Selection & Extension
Dedicated keys for selecting and extending text by character, word, or line, available on both the main matrix and thumb clusters.
```

### Key Features:

#### 1. VIM-Style Arrow Keys (Right Home Row)
The right home row becomes arrow keys, keeping your hands in optimal typing position (Dvorak Positions):
- **D position** (Index Inner): **Home** Key
- **H position** (Index): **←** Left Arrow
- **T position** (Middle): **↑** Up Arrow
- **N position** (Ring): **↓** Down Arrow
- **S position** (Pinky): **→** Right Arrow
- **Why?** Middle finger (longest) maps to Up, Ring finger to Down, following natural hand contour.

#### 2. Bidirectional Text Selection (Thumb Cluster)
Smart macros that select/extend text, placed on the thumbs for easy "pinching" with the index finger:

**Left Thumbs**:
- **Inner Thumb**: **Select Line** (Shift reverses direction)
- **Outer Thumb**: **Select Word** (Shift reverses direction)

**Right Thumbs**:
- **Inner Thumb**: **Extend Word** (Shift reverses direction)
- **Outer Thumb**: **Extend Line** (Shift reverses direction)

**Select All** (Left Ring Finger, Bottom Row):
- Useful for pinch-to-copy gestures (Thumb works Select All, Index triggers Copy).

#### 3. Stacked Editing Keys (Left Inner Column)
Copy and Paste keys are stacked vertically to allow the index finger to rake down:
- **Row 2**: **Cut**
- **Row 3**: **Copy**
- **Row 4**: **Paste**

#### 4. Find Operations (Bottom Row)
Quick access to search commands:
- **Find** (Index): Opens find dialog (Cmd+F)
- **Find Next** (Inner Index): Cycles to next match (Cmd+G)
- **Find Previous** (Right Bottom Row): Cycles to previous match (Cmd+Shift+G)
- **Shift + press**: Selects from cursor to **beginning of line**
- **How it works**: Jumps to line boundaries, then selects to the opposite end

#### 3. Find Operations (Bottom Row)
Quick access to search commands:
- **Find** (third from left): Opens find dialog (Cmd+F)
- **Find Next** (fourth from left): Cycles to next match (Cmd+G)
- **Find Previous** (right bottom row): Cycles to previous match (Cmd+Shift+G)

#### 4. Extend Selection (Right Bottom Row)
Dynamically grow existing selections:

**Extend Word** (second from right):
- **Normal press**: Extends selection **one word to the right**
- **Shift + press**: Extends selection **one word to the left**
- **Use case**: Select a word, then keep pressing to grow selection by words

**Extend Line** (third from right):
- **Normal press**: Extends selection **one line down**
- **Shift + press**: Extends selection **one line up**
- **Use case**: Select text, then keep pressing to grow selection by lines

#### 5. One-Handed Editing Shortcuts (Left Hand)
Ergonomic editing shortcuts on the left hand (row 2 & 3):
- **Row 2**: Enter, Space, Tab, Backspace, Cut
- **Row 3**: Copy, Paste, Undo, Redo
- **Why one-handed?** Allows you to use the mouse or touchpad with your right hand while editing with your left

#### 6. Advanced Navigation (Right Row 3)
Word and paragraph jumping with Command/Option modifiers:
- **⌥←** (Option+Left): Jump to previous word
- **⌘←** (Cmd+Left): Jump to beginning of line/paragraph
- **⌘↓** (Cmd+Down): Jump to end of document
- **⌘↑** (Cmd+Up): Jump to beginning of document
- **⌥→** (Option+Right): Jump to next word

### Usage Examples:

#### Example 1: Select Multiple Words
1. Hold **Cursor layer key** (bottom-right corner)
2. Press **Select Word** to select the current word
3. Keep holding Cursor layer, press **Extend Word** multiple times to grow selection
4. Release to return to base layer

#### Example 2: Find and Replace Workflow
1. Hold **Cursor layer key**
2. Press **Find** to open find dialog (Cmd+F)
3. Type search term, press Enter
4. While holding Cursor layer, use **Find Next**/**Find Prev** to cycle through matches
5. Use **Undo**/**Redo** to manage changes

#### Example 3: VIM-Style Navigation + Editing
1. Hold **Cursor layer key**
2. Use **D-H-T-N** (VIM arrows) to navigate
3. Press **Select Word** to select text
4. Press **Cut** or **Copy** (left hand stays on Cursor layer)
5. Navigate with arrows, then **Paste**

#### Example 4: One-Handed Text Manipulation
1. Hold **Cursor layer key** with right pinky
2. Left hand controls: Select, Copy, Paste, Undo, Redo
3. Right hand stays free for mouse/touchpad
4. Switch between editing actions without leaving Cursor layer

### Implementation Details:

**Macro Timing:**
- Selection macros use `wait-ms = 10` and `tap-ms = 10` for optimal speed
- If macros execute too fast/slow in your applications, timing can be adjusted in `config/macros.dtsi`

**Mod-Morph Behaviors:**
- Select Word/Line and Extend Word/Line use mod-morph to detect Shift modifier
- Allows bidirectional selection without additional keys
- Defined in `config/adv360.keymap` behaviors section

**Layer Activation:**
- Momentary layer (hold to activate, release to deactivate)
- No conflict with Nav layer (different activation key)
- Backslash (\\) still accessible via Symbol layer

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
