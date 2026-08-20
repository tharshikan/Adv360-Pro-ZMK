# Advanced Vim-Cut Navigation Layer

> **⚠️ Superseded (2026-08-20).** This documents the old macro-based `text_navigation`
> layer (still layer 9, but no longer reachable from the Sunaku base). The current
> vim engine is **Text Nav 2** (layer 15, Meh-chord protocol, interpreted by
> [hammerspoon-tharshi](https://github.com/tharshikan/hammerspoon-tharshi)) — see the
> [README](README.md#text-nav-2--the-vim-layer) for the live diagrams.

The `text_navigation` layer on your Adv360 has been completely overhauled to emulate Vim's highly efficient text editing paradigm, while preserving modern IDE integrations. 

This layer strictly separates concerns between hands:
* **The Right Hand (Mover)**: Exclusively handles cursor navigation, text highlighting, and line/word level cutting (deletes).
* **The Left Hand (Shaker)**: Exclusively handles clipboard management, window/tab navigation, and global file operations.

## Keyboard Layout Diagram

The visual representations below demonstrate the operations assigned to the physical keys in your 5x3 finger clusters on the `text_navigation` layer.

### Left Hand (Global & Editing)

| Row | Outer Pinky (`Tab/Esc/Shift`) | Pinky (`Q/A/Z`) | Ring (`W/S/X`) | Middle (`E/D/C`) | Index (`R/F/V`) | Inner Index (`T/G/B`) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Top** | Select to End of Line | Spotlight | Previous Tab | Next Tab | Close Tab | Reopen Tab |
| **Home**| Move to End of Line | Undo | Paste | Copy | Redo | Duplicate Line |
| **Bot** | Select Paragraph Above | Select Word Left | Select Line Above | Select Line Below | Select Word Right| Select Paragraph Below |

> **Note:** The left hand replaces standard modifier keys with highly-efficient macro sequences. For example, instead of pressing `Cmd + C` to copy, simply holding the navigation layer toggle and tapping the Left Middle finger (`Paste`) accomplishes the full sequence instantly.

---

### Right Hand (Vim-Navigation & Selection)

| Row | Inner Index (`Y/H/N`) | Index (`U/J/M`) | Middle (`I/K/,`) | Ring (`O/L/.`) | Pinky (`P/;/slash`) | Outer Pinky (`]/\|/'`) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Top** | Select to Start | **[LEFT ARROW]** | **[VISUAL MODE]** | Undo | **[RIGHT ARROW]** | Select to End |
| **Home**| Move to Start | Move Word Left | Move Line Down | Move Line Up | Move Word Right | Move to End |
| **Bot** | **[CUT LINE]** | **[CUT WORD]** | Insert Line Below| Insert Line Above| Redo | **[CUT LINE END]** |

> **Note:** The Right Hand layout is built symmetrically:
> * **Home Row:** Instant cursor jumps using `Option` and `Cmd` arrows behind the scenes.
> * **Top Row:** Identical directional jumps as the Home Row, but holding `Shift` internally to instantly highlight text as you navigate.
> * **Bottom Row (The Vim Engine):** Tapping these keys triggers custom ZMK macros that instantly select the entire word/line in that direction and execute an OS-level cut command (`Cmd + X`), mimicking Vim's behavior where deleted text is preserved in the clipboard for immediate pasting elsewhere.

## Vim-Cut Engine Specifics
The custom firmware macros added to `macros.dtsi` completely bypass macOS limitations by performing multi-step operations on a single keypress:

* **Cut Word Left:** `Option + Backspace` (was `Option + Shift + Left Arrow` -> `Cmd + X`; the
  select-then-cut form had no meaning in a terminal, see the [README](README.md#text-nav-2--the-vim-layer))
* **Cut Entire Line:** `Cmd + Left Arrow` -> `Shift + Cmd + Right Arrow` -> `Cmd + X`

With this complete decoupling, your right hand can freely delete sentences and move the cursor, while the left hand drops the preserved text gracefully into its new home.

---

## Visual Mode Layer (`visual_navigation`)
When you tap the **[VISUAL MODE]** key, the keyboard automatically selects the current word and locks into this temporary layer. All movement keys are shifted, allowing you to instantly expand your selection endlessly without holding down any modifier keys. 

### Left Hand (Visual Window & Copying)

| Row | Outer Pinky (`Tab/Esc/Shift`) | Pinky (`Q/A/Z`) | Ring (`W/S/X`) | Middle (`E/D/C`) | Index (`R/F/V`) | Inner Index (`T/G/B`) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Top** | Select to End of Line | Spotlight | Previous Tab | Next Tab | Close Tab | Reopen Tab |
| **Home**| Move to End of Line | Undo | **[VISUAL CUT & EXIT]** | **[VISUAL COPY & EXIT]** | Redo | Duplicate Line |
| **Bot** | Select Paragraph Above | Select Word Left | Select Line Above | Select Line Below | Select Word Right| Select Paragraph Below |

> **Note:** Tap the Copy key to instantly capture your highlighted selection to the clipboard and snap out of Visual Mode.

### Right Hand (Visual Extending & Cutting)

| Row | Inner Index (`Y/H/N`) | Index (`U/J/M`) | Middle (`I/K/,`) | Ring (`O/L/.`) | Pinky (`P/;/slash`) | Outer Pinky (`]/\|/'`) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Top** | Select to Start | **[EXPAND LEFT]** | **[TOGGLE EXIT VISUAL]**| Undo | **[EXPAND RIGHT]** | Select to End |
| **Home**| Move to Start | **[EXPAND WORD LEFT]** | **[EXPAND DOWN]** | **[EXPAND UP]** | **[EXPAND WORD RIGHT]** | Move to End |
| **Bot** | **[WRAP PARENS]** | **[WRAP QUOTES]** | **[VISUAL CUT]**| **[VISUAL COPY]**| **[WRAP BRACKETS]** | **[WRAP BRACES]** |

> **Note:** Tapping any **CUT** or **COPY** command will perform the action and automatically return you to the standard navigation layer. If you decide to cancel the manipulation, tap the main [TOGGLE EXIT VISUAL] mapped to the `L` position (or the `Esc` key on either thumb cluster) to drop the cursor and exit manually.

## The Stateful Visual Mode (`v`)
True Vim-style highlighting is achieved via a dedicated hidden `visual_navigation` layer.

Because macOS natively discards highlights when bare arrow keys are struck, the firmware intercepts your directional inputs and translates them continuously using macros.

1. **Enter Visual Mode:** Press `Visual Mode Enter` (mapped to `L` on the `text_navigation` right hand). The keyboard selects the current word via `mac_sel_word` and toggles into the hidden `visual_navigation` layer.
2. **Move:** All right-hand movement keys now act as `Shift` variants automatically. Pressing `Up Arrow` sends `Shift + Up Arrow`, extending your selection indefinitely. 
3. **Execute:** The moment you strike any cut key (`C`, `X`, or the Vim-cut engine keys) or press `Esc`, the keyboard executes the action, toggles `visual_navigation` back off, and returns to the normal `text_navigation` layer as long as you are still holding the navigation-layer key.
