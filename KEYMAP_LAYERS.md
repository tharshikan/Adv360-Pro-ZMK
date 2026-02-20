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
- [Layer 6: OptNav Layer](#layer-6-optnav-layer)
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
| 6 | opt_nav | OptNav | **Option** + Arrows/Nav Keys (Word Navigation) | **Hold Right Thumb ']'** |

---

## Layer Access

### Layer Switching Keys
- **`sl 1`**: Sticky Layer 1 (Symbols+Numpad) - activates for next keypress only.
- **`td_sym` (Smart Toggle)**: Replaces Page Down on the right thumb.
  - **Tap**: Acts as `sl 1` (Sticky Layer).
  - **Double Tap**: Toggles Layer 1 ON/OFF.
- **`sl 4` (Nav)**: **Left Thumb (Middle)**. Tap for Sticky (One-Shot), Hold for Momentary.
- **`lt_nav_enter` (Right Thumb)**: Tap for Enter, Hold for Nav Layer.
- **`lt 7` (Launcher)**: **Hold Left Arrow** to activate App Launcher.

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
│  ESC   │ A  │ O  │E/Sft│I/L8│ G  │        │                                       │        │ D  │H/L8│ T  │ N  │ S  │ SL(1) │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ SHIFT  │ X  │ J  │ ,  │ =  │  '          │                                       │           C │ M  │ V  │ W  │ .  │ SHIFT │
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────┼────┼────┼────┼───────┴┐
  │CurTog│  /   │ Z  │ ^/L7 │  ?                                                                    │  (   │  )   │  -   │ {/[  │ }/]  │
  └──────┴────┴────┴────┘                                                                            └────┴────┴────┴───────┘

             Left Thumb Cluster                                                   Right Thumb Cluster
            ┌──────────────┐                                                     ┌──────────────┐
            │   SMART_BSPC │                                                     │   RCTRL      │
            │ (Hold Shift) │                                                     │              │
            ├──────────────┤                                                     ├──────────────┤
            │   SL 4 (Nav) │                                                     │   TD_SYM     │
            ├──────────────┤                                                     ├──────────────┤
            │    TD_SYM    │                                                     │   TD_SYM     │
            ├──────┬───────┤                                                     ├──────┬───────┤
            │ ESC  │  TAB  │                                                     │ END  │KP_DOT│
            ├──────┼───────┤                                                     ├──────┬───────┤
            │ BSPC │ SL 4  │                                                     │ NAV/ │ SPACE │
            │      │       │                                                     │ ENTER│       │
            └──────┴───────┘                                                     └──────┴───────┘

```

### Key Features:
- **Snappy & Safe Thumb Cluster:**
  - **Space/Enter**: Instant fire (`quick-tap=0`) for typing speed.
  - **Backspace**: Requires `prior-idle` of 125ms to activate Shift (prevents accidental Shift during typos).
  - **Nav/Delete Keys**: High-performance optimization.
- **Improved Nav Layer Access:** 
  - **Left Thumb:** Dedicated Sticky/Momentary Toggle (`sl 4`). 
  - **Right Thumb:** Hold Enter for momentary access.
- **Layer 8 Access:** Hold `I` or `H` on the home row for Backup Sym layer.
- **Layer Toggles:** 
  - **CurTog**: Left Bottom Row (Index 1) & Right Bottom Row (Index 2).
  - **SymTog**: Left Thumb, Right Thumb, Right Bottom Row (x2).
- **Launcher:** Activated by **Hold BSLH** (Backslash) on Left Bottom Row.
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
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│   =    │ 1  │ <  │ >  │ 4  │ 5  │  Trans │                                       │ MO(3)  │ 6  │ 7  │ 8  │9/[ │0/] │   -   │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│  TAB   │ !  │ @  │ #  │ $  │ %  │        │                                       │        │ \  │ <  │ >  │ [  │ ]  │   \   │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│  ESC   │ *  │ +  │ =  │ -  │ ^  │        │                                       │        │ "  │ (  │ )  │ {  │ }  │   '   │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ SHIFT  │ ~  │ &  │ |  │ \  │ `           │                                       │           # │ .  │ ?  │ :  │ ;  │ SHIFT │
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────┼────┼────┼────┼───────┴┐
  │MO(2) │Trans │Trans │Trans │Trans                                                                  │Trans │Trans │Trans │Trans │MO(2) │
  └──────┴────┴────┴────┘                                                                                 └──────┴──────────┴──────────┴────────┘
```

---

## Layer 4: Nav Layer

**Display Name:** Nav
**Purpose:** Navigation Arrows, Shortcuts (Copy/Paste), and Command Modifiers
**Access:** **Left Thumb** (Sticky/Hold `sl 4`) OR **Right Thumb** (Hold Enter)

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│ CMD+1  │CMD1│CMD2│CMD3│CMD4│CMD5│        │                                       │        │CMD6│CMD7│CMD8│CMD9│CMD0│ CMD+[ │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│ CMD+Tab│CMDQ│CMDP│CMDU│CMDY│CMD;│        │                                       │        │CMDK│CMDL│CMDT│CMDR│CMDB│ CMD+\ │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│ CMD+Esc│CMDA│CMDO│CMDE│CMDI│CMDG│        │                                       │        │CMDD│ ←  │ ↓  │ ↑  │ →  │       │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ CMD+Sft│Undo│Cut │Copy│Pste│CMD'         │                                       │             │CMDC│CMDM│CMDW│CMDV│CMDF │ CMD+Sft│
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
- **Shifted VIM-Style Arrows**: Arrow keys are shifted one column to the right (to H/T/N/S positions) compared to standard VIM (usually H/J/K/L, but here aligned with Dvorak home row).
    - **Index Inner (D):** `Command + D`
    - **Index (H):** `Left Arrow`
    - **Middle (T):** `Down Arrow`
    - **Ring (N):** `Up Arrow`
    - **Pinky (S):** `Right Arrow`


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
├────────┼────────┼────────┼────────┼────────┼────────┼────────┤                                       ├────────┼──────┼──────┼──────┬───────┼───────┼───────┤
│ Search │ Sft(S) │  Redo  │  Undo  │  BSPC  │  Cut   │ WinMsn │                                       │        │ Cut  │ BSPC │ Undo │ Redo  │ Sft(S)│ Search│
├────────┼────────┼────────┼────────┼────────┼────────┤ Ctrl   │                                       │  Tab   ├──────┼──────┼──────┼───────┼───────┼───────┤-------------------------------------------------------------------------------------------------------------------------------
│ CMD+Tab│  GUI   │  Alt   │  Ctrl  │ Shift  │ Copy │ CtrlTab│  Tab   │ trans  │ trans  │ trans  │ trans  │ Copy │ Left   │ Down   │ Up     │ Right  │ CMD+L  │
├────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┼────────┤
│ DwnLd  │ SelAll │ SelLn  │ SelWd  │  Find  │ Paste           │                                       │ Paste         │ Home │ PgUp │ PgDn  │  End  │ DwnLd │
└─┬──────┼────────┼────────┼────────┼────────┴─────────────────┘                                       └───────────────┴──────┼──────┼───────┴───────┴───────┘
  │FindRep│  Prev  │ ExtLn  │ ExtWd  │  Next   │ SelWrd              ┌───────┐┌───────┐┌──────┐   ┌───────┐┌───────┐┌──────┐               │ Esc  │ ExtLn│ ExtWd │  Find │FindRep│
  └───────┴───────┴────────┴────────┴───────┘            │SelLin ││UnlckL5││UnlckL5│   │ Esc   ││ExtLn  ││ExtWrd│            └──────┴──────┴───────┴───────┴───────┘
                                                         └───────┘└───────┘└──────┘   └───────┘└───────┘└──────┘│SelNone││ExtLine││ExtWrd│

            Legend:
            Search   = Spotlight Search (Cmd+Space)
            URLBar   = Focus URL Bar (Cmd+L)
            DwnLd    = Downloads (Cmd+Opt+L)
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

- **Row 4 (Lower)**: `Downloads` | `Select All` | `Select Line` | `Select Word` | `Find` | `Paste`
- **Arrow Keys (Right Home)**: `CMD+D` | `Left` | `Down` | `Up` | `Right` (Ergonomic cluster).
- **Thumbs (Left)**:
    - **Big Keys**: `App Switcher` (Cmd+Tab), `Mission Control` (Ctrl+Up), `Unlock Layer` (Exit).
    - **Small Keys**: `Tab Switcher` (Ctrl+Tab), `Tab`.
- **Thumbs (Right)**:
    - **Big Keys**: `Esc`, `Extend Line`, `Extend Word`.


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

---

## Layer 6: OptNav Layer

**Display Name:** OptNav
**Purpose:** Word Navigation (Option + Arrows) and Word Deletion (Option + Backspace)
**Access:** **Hold** Right Thumb `]` Key

```
┌────────┬────┬────┬────┬────┬────┬────────┐                                       ┌────────┬────┬────┬────┬────┬────┬───────┐
│ OPT+1  │OPT1│OPT2│OPT3│OPT4│OPT5│        │                                       │        │OPT6│OPT7│OPT8│OPT9│OPT0│ OPT+[ │
├────────┼────┼────┼────┼────┼────┼────────┤                                       ├────────┼────┼────┼────┼────┼────┼───────┤
│ OPT+Tab│OPTQ│OPTP│OPTU│OPTY│OPT;│        │                                       │        │OPTK│OPTF│OPTL│OPTR│OPTB│ OPT+\ │
├────────┼────┼────┼────┼────┼────┤        │                                       │        ├────┼────┼────┼────┼────┼───────┤
│ OPT+Esc│OPTA│OPTO│OPTE│OPTI│OPTG│        │                                       │        │OPTD│OPT←│OPT↓│OPT↑│OPT→│       │
├────────┼────┼────┼────┼────┼────┴────────┤                                       ├────────┴────┼────┼────┼────┼────┼───────┤
│ OPT+Sft│OPTZ│OPTX│OPTC│OPTV│OPT'         │                                       │           OPTC│OPTM│OPTW│OPTV│OPT.│ OPT+Sft│
└─┬──────┼────┼────┼────┼────┴─────────────┘                                       └─────────────┴────┼────┼────┼────┼───────┴┐
  │      │OPTX│OPTZ│OPT←│OPT→                                                                         │OPT↑│OPT↓│OPT]│OPT\│      │
  └──────┴────┴────┴────┘                                                                             └────┴────┴────┴───────┘
                                                       ┌───────┐
                                                       │OPT+BSP│
                                                       └───────┘
```

### Key Features:
- **Same Layout as Nav Layer**, but with **Option (Alt)** modifier instead of Command.
- **Option + Arrows**: Move cursor by word (Left/Right) or paragraph (Up/Down).
- **Option + Backspace**: Delete entire word (to the left).

---
## Performance Tuning
This configuration is optimized for high-speed typing with minimal latency ("Snappy Mode").

### 1. Eager Debouncing
- **Latency**: 0ms Press / 5ms Release
- **Effect**: Alphanumeric keys fire the instant the switch actuates.

### 2. Thumb Cluster Response
- **Space & Enter**:
    - **Quick Tap**: 0ms (Instant fire on tap)
    - **Debounce**: Optimized for fast repeats
- **Backspace**:
    - **Safety**: 125ms idle timeout prevents accidental Shift activation.
- **Nav Layer**:
    - **Activation**: Zero-latency Sticky Layer (`sl 4`) on left thumb.

---
*Generated from ZMK firmware configuration for Kinesis Adv360 Pro*
