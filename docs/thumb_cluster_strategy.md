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
| **Outer (Large)** | **Backspace** / L4 | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• `idle: 160ms`<br>• Term: **220ms** | Standard fast Backspace, holds for Nav Layer 4. |
| **Inner (Large)** | **Escape** / LCTRL | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• `idle: 140ms`<br>• Term: **220ms** | Convenient Control access on hold, Escape on tap. |
| **Small (Bottom)** | **Escape** / LALT | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• `idle: 140ms`<br>• Term: **200ms** | Option (Alt) modifier access on the lowest thumb key. |

### Right Thumb Cluster

| Key (Position) | Function | Behavior | Configuration | Why? |
| :--- | :--- | :--- | :--- | :--- |
| **Inner (Large)** | **Enter** / RCTRL | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• Term: **175ms**<br>• `quick-tap: 0` | Fast **175ms** for rapid Enter usage. Holds for Control. |
| **Outer (Large)** | **Space** / L3 | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• Term: **190ms**<br>• `quick-tap: 0` | **The Speed King.** <br>• **190ms:** Extremely fast for Space.<br>• **QT=0:** Disables double-tap logic for instant firing. Holds for Layer 3. |
| **Small (Bottom)** | **Tab** / LALT | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• `idle: 140ms`<br>• Term: **200ms** | Tab on tap, Option (Alt) on hold. |

---

## Operational "Feel"

1.  **Typing (Space/Backspace):**
    *   Feels almost indistinguishable from a standard "dumb" keyboard.
    *   Fires instantly (`quick-tap: 0` on Space).
    *   Forgives clumsy/long presses (`retro-tap` + high `tapping-term`).

2.  **Layer/Mod Access (Control/Option/Nav):**
    *   Requires a **deliberate** pause/hold.
    *   You cannot simply "flick" the layer on; you must press-and-hold for a split second to engage the modifier.

---

## Home Row Modifiers (HRMs) Configuration

To complement the thumb cluster, the home row incorporates specialized modifiers (Symbol Layer, Shift, and positional modifiers) configured for **accuracy and speed** without accidental triggers.

### Settings Breakdown

| Parameter | Value | Purpose |
| :--- | :--- | :--- |
| **Flavor** | `tap-preferred` | `tap-preferred` is used globally to prioritize typing the character if rolled quickly. |
| **Require Prior Idle** | `150ms` | Extremely strict safety measure. A modifier will *only* activate if you haven't typed *any* other key for 150ms prior. |
| **Quick Tap** | `180ms-200ms` | Allows rapid double-tapping to repeat a key without accidentally triggering the modifier. |
| **Hold-Trigger-On-Release** | Enabled | Critical component of "Timeless" HRMs. Evaluates mod-tap resolution on key *release* instead of press, fixing same-hand chording. |
| **Retro Tap** | Enabled | Holding the key past the tapping term but *not* pressing another key will still output the base key upon release. |

### Bilateral Combinations (Cross-Hand Required)

To completely eliminate same-hand misfires during fast typing "rolls", **all** standard home row modifiers (Shift, Symbol Layer, Command, Option, Control) strictly use **Bilateral Combinations**.

This means a left-hand modifier will **only** activate if the next key pressed is on the right hand (and vice versa). This is achieved via ZMK's `hold-trigger-key-positions` arrays acting alongside `hold-trigger-on-release`.

### Staggered Tapping Terms & Specific Modifiers

Tapping terms are staggered based on finger strength and dexterity:

*   **Pinky (A, X):** `350ms`/`250ms` (Highest timeout on home row to resist accidental triggers).
*   **Pinky Right (S, DOT):** `250ms`/`243ms`
*   **Ring Left (O, J):** `270ms`/`250ms`
*   **Ring Right (N, V):** `243ms`
*   **Middle (E, T):** `260ms`/`243ms`
*   **Index (I, H):** `260ms`/`234ms` (Fastest, most deliberate)
