# Advanced Vim-Cut Navigation Layer

The `text_navigation` layer on your Adv360 has been completely overhauled to emulate Vim's highly efficient text editing paradigm, while preserving modern IDE integrations. 

This layer strictly separates concerns between hands:
* **The Right Hand (Mover)**: Exclusively handles cursor navigation, text highlighting, and line/word level cutting (deletes).
* **The Left Hand (Shaker)**: Exclusively handles clipboard management, window/tab navigation, and global file operations.

## Keyboard Layout Diagram

The visual representations below demonstrate the operations assigned to the physical keys in your 5x3 finger clusters on the `text_navigation` layer.

### Left Hand (Global & Editing)

| Row | Pinky (`Q/A/Z`) | Ring (`W/S/X`) | Middle (`E/D/C`) | Index (`R/F/V`) | Inner Index (`T/G/B`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Top** | Spotlight | Previous Tab | Next Tab | Close Tab | Reopen Tab |
| **Home**| Undo | Paste | Copy | Redo | Duplicate Line |
| **Bot** | Find / Search | Find Previous | Find Next | Format Document| Select All |

> **Note:** The left hand replaces standard modifier keys with highly-efficient macro sequences. For example, instead of pressing `Cmd + C` to copy, simply holding the navigation layer toggle and tapping the Left Middle finger (`Paste`) accomplishes the full sequence instantly.

---

### Right Hand (Vim-Navigation & Selection)

| Row | Inner Index (`Y/H/N`) | Index (`U/J/M`) | Middle (`I/K/,`) | Ring (`O/L/.`) | Pinky (`P/;/slash`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Top** | Select to Start | Select Word Left | Select Line Down | Select Line Up | Select Word Right |
| **Home**| Move to Start | Move Word Left | Move Line Down | Move Line Up | Move Word Right |
| **Bot** | **[CUT LINE]** | **[CUT WRD LFT]** | Add Cursor Below| Add Cursor Above| **[CUT WRD RGT]** |

> **Note:** The Right Hand layout is built symmetrically:
> * **Home Row:** Instant cursor jumps using `Option` and `Cmd` arrows behind the scenes.
> * **Top Row:** Identical directional jumps as the Home Row, but holding `Shift` internally to instantly highlight text as you navigate.
> * **Bottom Row (The Vim Engine):** Tapping these keys triggers custom ZMK macros that instantly select the entire word/line in that direction and execute an OS-level cut command (`Cmd + X`), mimicking Vim's behavior where deleted text is preserved in the clipboard for immediate pasting elsewhere.

## Vim-Cut Engine Specifics
The custom firmware macros added to `macros.dtsi` completely bypass macOS limitations by performing multi-step operations on a single keypress:

* **Cut Word Left:** `Option + Shift + Left Arrow` -> `Cmd + X`
* **Cut Word Right:** `Option + Shift + Right Arrow` -> `Cmd + X`
* **Cut Entire Line:** `Cmd + Left Arrow` -> `Shift + Cmd + Right Arrow` -> `Cmd + X`

With this complete decoupling, your right hand can freely delete sentences and move the cursor, while the left hand drops the preserved text gracefully into its new home.
