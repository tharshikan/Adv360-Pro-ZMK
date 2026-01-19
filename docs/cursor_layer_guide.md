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
| **Extend Word** | Right Inner Thumb | Grows selection by one word (Forward). |
| **Extend Line** | Right Outer Thumb | Grows selection by one line (Down). |

## 3. Structural Editing

### Left Hand Generation
*   **Select Paragraph:** Row 2 (Middle). **New!** Selects the entire paragraph block.
*   **Select Next (`Cmd+D`):** Bottom Row (Index). Selects the next instance of the current word.

### Right Hand Navigation
*   **Extend Prev Word:** Inner Column Row 3. **New!** Extends selection left (backwards).
*   **Extend Prev Line:** Inner Column Row 2. **New!** Extends selection up.
*   **Delete Word:** Row 2 (Index).

### Formatting
*   **Comment Code (`Cmd+/`):** Inner Column Bottom.

## 4. The "Editing Stack" (Left Hand)
Your left index finger controls a vertical stack of editing commands.
*   **Cut:** Top Row (`Y` pos)
*   **Copy:** Home Row (`I` pos)
*   **Paste:** Bottom Row (`K` pos)

## Cheatsheet Summary

**Right Hand (Movement & Destruction):**
*   `H/T/N/S`: Arrows
*   `Inner Col`: Extend Back/Up, Comment

**Left Hand (Action Powerhouse):**
*   `Y/I/K`: Cut/Copy/Paste
*   `Del Word`: Row 2 (Index)
*   `Sel Para`: Row 2 (Middle)
