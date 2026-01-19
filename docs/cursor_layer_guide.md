# Cursor Layer Efficiency Guide (Layer 5)

The **Cursor Layer** is your "Editor Mode". Unlike the Nav layer (which is for system navigation), the Cursor layer is optimized for **text manipulation**, **selection**, and **coding**.

**Activation:** Tap **Page Down** (Right Thumb) to enter "Sticky" mode, or **Double-Tap** to "Lock" it.

## 1. "VIM-Style" Arrow Keys
Move the cursor without leaving the home row. Note that these are shifted one key to the right compared to standard VIM (H/J/K/L) to align with your Dvorak home row fingers.

*   **Left (`←`):** Index Finger
*   **Down (`↓`):** Middle Finger
*   **Up (`↑`):** Ring Finger
*   **Right (`→`):** Pinky Finger

## 2. The "Selection" Engine
This layer turns your thumbs into text selection tools. You can "pinch" text to select it.

| Action | Key (Thumb) | Effect |
| :--- | :--- | :--- |
| **Select Word** | Left Outer Thumb | Selects current word. |
| **Select Line** | Left Inner Thumb | Selects entire line. |
| **Extend Word** | Right Inner Thumb | Grows selection by one word. |
| **Extend Line** | Right Outer Thumb | Grows selection by one line. |

## 3. Structural Editing (New!)
We have optimized the layout for "selecting blocks" and "destroying blocks".

### Selection Cluster (Left Hand Bottom)
*   **Select Paragraph:** Bottom Left Corner. **New!** Selects the entire paragraph block.
*   **Select Next (`Cmd+D`):** Bottom Row (Index). Selects the next instance of the current word.
*   **Select Word:** Bottom Row (Left).
*   **Select All:** Bottom Row (Outer).

### Destruction Cluster (Right Hand Bottom)
*   **Delete Word (`Opt+Bsp`):** Bottom Row (Inner Inder). **New!** Deletes the word to the left of cursor.
*   **Home/End/PgUp/PgDn:** Remainder of the bottom row.

### Formatting
*   **Comment Code (`Cmd+/`):** Inner Column (Right). **New!** Toggles comments on the current line or selection.

## 4. The "Editing Stack" (Left Hand)
Your left index finger controls a vertical stack of editing commands.
*   **Cut:** Top Row (`Y` pos)
*   **Copy:** Home Row (`I` pos)
*   **Paste:** Bottom Row (`K` pos)

## 5. Tab & App Navigation (Left Inner)
Navigate tabs and apps with your left index/inner fingers.
*   **Next Tab:** Row 3 (`Ctrl+Tab`)
*   **Prev Tab:** Row 4 (`Ctrl+Shift+Tab`)
*   **Mission Control:** Row 2 (`Ctrl+Up`)

## Cheatsheet Summary

**Right Hand (Movement & Destruction):**
*   `H/T/N/S`: Arrows
*   `Del Word`: Bottom Row (Start)
*   `Comment`: Inner Column

**Left Hand (Selection & Action):**
*   `Y/I/K`: Cut/Copy/Paste
*   `Select Next`: Bottom Row (Middle)
*   `Select Paragraph`: Bottom Corner
