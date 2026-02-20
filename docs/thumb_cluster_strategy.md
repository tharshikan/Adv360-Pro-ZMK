# Thumb Cluster & Home Row Strategy: "Snappy & Safe"

This document outlines the specific ZMK configuration strategy used for the Thumb Clusters and Home Row Modifiers. The goal is to maximize **typing speed and responsiveness** ("Snappiness") for primary actions (Space, Backspace, Enter) and standard typing while preventing accidental layer/modifier activations or missed keys.

## Core Philosophy

### 1. Tap-Preferred (`flavor = "tap-preferred"`)
**Priority:** Tapping > Holding.
The keyboard aggressively assumes you want the **Tap** action (Space/Backspace) even if you are typing so fast that you "roll" your fingers (overlappingly hold the thumb key while hitting the next letter).

### 2. Retro-Tap (`retro-tap`)
**The Safety Net.**
If you hesitate and hold a thumb key longer than its timeout but **don't** press any other key, releasing it will strictly send the **Tap** action.
*   *Solves:* "Space not registering" when lingering on the key.
*   *Behavior:* Hold Space (300ms) -> Release -> Output: "Space" (Instead of nothing).

---

## Configuration Details

### Left Thumb Cluster

| Key (Position) | Function | Behavior | Configuration | Why? |
| :--- | :--- | :--- | :--- | :--- |
| **Inner (Large)** | **Backspace** / Shift | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• `idle: 125ms`<br>• Term: **220ms** | **220ms** window for sloppy presses<br>**Idle Check** ensures rapid typos trigger Backspace, not Shift. |
| **Middle** | **Nav Layer** (4) | `sticky-layer` | • `&sl 4`<br>• N/A | **Native ZMK Sticky Layer.**<br>• **Tap:** One-Shot Layer (Sticky).<br>• **Hold:** Momentary Layer.<br>• Removed complex `hold-tap` logic. |
| **Outer** | **Escape** | `kp` | • Standard | Simple key press, no behavior logic needed. |

### Right Thumb Cluster

| Key (Position) | Function | Behavior | Configuration | Why? |
| :--- | :--- | :--- | :--- | :--- |
| **Inner (Large)** | **Enter** / Layer 4 | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• Term: **175ms**<br>• `quick-tap: 0` | Fast **175ms** for rapid Enter usage. `tap-preferred` + `QT=0` ensures Enter fires instantly like Space. |
| **Middle** | **Space** / Shift | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• Term: **225ms**<br>• `quick-tap: 0` | **The Speed King.** <br>• **225ms:** Extremely forgiving for Space.<br>• **QT=0:** Disables double-tap logic for instant firing.<br>• **Tap-Pref:** Never misses a space during fast typing. |
| **Outer** | **Backup Sym Toggle** | `tap-dance` | • Term: **175ms** | Standard reliable toggle for standard symbol layer access. |

---

## Operational "Feel"

1.  **Typing (Space/Backspace):**
    *   Feels almost indistinguishable from a standard "dumb" keyboard.
    *   Fires instantly (`quick-tap: 0` on Space).
    *   Forgives clumsy/long presses (`retro-tap` + high `tapping-term`).

2.  **Layer Access (Shift/Nav):**
    *   Requires a **deliberate** pause/hold.
    *   You cannot simply "flick" the layer on; you must press-and-hold for a split second (approx 0.2s) to engage the modifier.

---

## Home Row Modifiers (HRMs) Configuration

To complement the thumb cluster, the home row incorporates specialized modifiers (Symbol Layer, Shift, and positional modifiers) configured for **accuracy and speed** without accidental triggers.

### Settings Breakdown

| Parameter | Value | Purpose |
| :--- | :--- | :--- |
| **Flavor** | `balanced` / `tap-preferred` | `balanced` on standard HRMs resolves holds/taps based on whether the key was pressed within overlapping times. `tap-preferred` is used for Shift (`E`) and Symbol Layer (`I`, `H`) to prioritize typing the character if rolled quickly. |
| **Require Prior Idle** | `160ms` | Extremely strict safety measure. A modifier will *only* activate if you haven't typed *any* other key for 160ms prior. Eliminates almost all accidental mods during fast typing rolls. |
| **Quick Tap** | `175ms` | Allows rapid double-tapping to repeat a key (e.g., typing "ee" or "ll" quickly) without accidentally triggering the modifier. |
| **Hold-Trigger-On-Release** | Enabled | Used with Positional Holds. Allows releasing the modifier key *after* you release the triggered key without accidentally outputting the modifier's base key character. |
| **Retro Tap** | Enabled | Specifically for the `E`, `I` and `H` modifiers; holding the key past the tapping term but *not* pressing another key will still output the base key upon release. |

### Bilateral Combinations (Cross-Hand Required)

To completely eliminate same-hand misfires during fast typing "rolls", **all** standard home row modifiers (Shift, Symbol Layer, Command, Option, Control) strictly use **Bilateral Combinations**.

This means a left-hand modifier will **only** activate if the next key pressed is on the right hand (and vice versa). This is achieved via ZMK's `hold-trigger-key-positions` arrays. 

### Staggered Tapping Terms & Specific Modifiers

Tapping terms are staggered based on finger strength and dexterity, and some specific modifiers have custom overrides to prevent accidental activation by weaker, slower fingers:

*   **Pinky (A, S/Command):** `350ms` (Highest timeout. Extremely resistant to accidental triggers on slow outer fingers, but fast tapping remains snappy due to tap-preferred logic).
*   **Pinky (Standard):** `280ms` (Slowest, most forgiving)
*   **Ring:** `240ms`
*   **Middle:** `210ms`
*   **Index:** `180ms` (Fastest, most deliberate)
*   **Symbol Layer & Shift (H, I, T, E):** `225ms` with `tap-preferred` and `retro-tap` for high-accuracy standard typing retention, independent of positional holds.
