# design: Cursor Layer Phase 2 (Advanced Editing)

You requested a design for "highlight/unhighlight by paragraph", "delete word", and other advanced editing features.

## 1. The Core Philosophy
We want to move from "Text Selection" to "Structural Editing". Instead of just selecting characters, we select *units* of code (words, lines, paragraphs, scopes).

## 2. Proposed Features

### A. Advanced Selection
*   **Select Paragraph:** Crucial for moving blocks of text.
    *   *Macro:* `Option + Shift + Up` (Select to start of paragraph) / `Down` (End).
    *   *Alternative:* `Cmd + Shift + Down` (Select to end of text block).
*   **Select Scope (Expand Selection):** Smart selection that grows from `word` -> `string` -> `brackets` -> `function`.
    *   *Macro:* `Control + Command + Shift + Right` (IntelliJ/VSCode "Expand Selection").

### B. "Destructive" Editing
*   **Delete Word:** `Option + Backspace`.
*   **Delete Line:** `Command + Backspace`.
*   **Kill Line:** `Ctrl + K` (Emacs style, commonly supported).

### C. Coding Utilities
*   **Comment/Uncomment:** `Command + /`.
*   **Join Lines:** `Ctrl + J` (VSCode default is different, but we can standardise).
*   **Duplicate Line:** `Command + Shift + D` (or `Cmd + C` then `Cmd + V` x2, but dedicated is nicer).

## 3. Proposed Layout Updates

### Left Hand Updates
We can optimize the Bottom Row further.
*   **Current:** `Downloads` | `Select All` | `Select Next` | `Select Word` | `Find` | `Paste`
*   **Proposal:** Replace `Downloads` (rarely used) and `Select All` (redundant with Cmd+A usually) with "Smart Select".

### Right Hand Updates (The "Destruction" Cluster)
Currently, the Right Hand has `Home`, `PgUp`, `PgDn`, `End` on the bottom row.
We can use the **Top Row** or **Inner Column** for deletion.

*   **Delete Word:** High value target.
    *   *Prop:* Replace `Mac_Paste` (Right Bottom Row - currently redundant) with `Delete Word`.
*   **Delete Line:**
    *   *Prop:* Map to `Shift + Backspace` on the thumb?

### The "Formatting" Cluster
We need a place for "Comment Code".
*   *Prop:* Replace `Mac_Find` (Right Bottom Inner - wait, looking at keymap...)
    *   *Correction:* Right Bottom is `Paste`, `Home`, `PgUp`...
    *   We have a `trans` key in the Inner Column (Row 4 Right). Perfect spot for `Comment Code`.

## 4. Design Mockup

```
Left Hand (Selection):
Row 4:  [Sel Scope] [Sel Para] [Sel Next] [Sel Word] [Find] [Paste]
        (Grow)      (Block)    (Multi)    (Unit)

Right Hand (Destruction & Nav):
Row 4:  [Del Word]  [Home]     [PgUp]     [PgDn]     [End]  [Del Line]
        (Opt+Bsp)                                           (Cmd+Bsp)

Right Inner Column (Row 4):
[Comment Code] (Cmd+/)
```

## 5. Implementation Strategy
1.  **Define Macros:**
    *   `Mac_Del_Word`: `Option + Backspace`
    *   `Mac_Del_Line`: `Command + Backspace`
    *   `Mac_Sel_Para`: `Option + Shift + Down` (Repeated presses select paragraphs)
    *   `Mac_Comment`: `Command + /`
2.  **Update Keymap:**
    *   Swap `Mac_Paste` (Right Bottom) -> `Mac_Del_Word`.
    *   Swap `Downloads` -> `Mac_Sel_Para`.
    *   Inner Right -> `Mac_Comment`.

## 6. Feedback
This design focuses on **selecting blocks** (Left Hand) and **deleting blocks** (Right Hand), keeping a "Creation vs Destruction" symmetry.
