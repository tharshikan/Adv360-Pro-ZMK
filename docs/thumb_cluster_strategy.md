# Thumb Cluster Strategy: "Snappy & Safe"

This document outlines the specific ZMK configuration strategy used for the Thumb Clusters. The goal is to maximize **typing speed and responsiveness** ("Snappiness") for primary actions (Space, Backspace, Enter) while preventing accidental layer activations or missed keys.

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
| **Middle** | **Delete** / Layer 4 | `hold-tap` | • `balanced`<br>• Term: **200ms** | Kept `balanced` as Delete is a secondary action; prevents accidental Layer 4 activation during editing. |
| **Outer** | **Escape** | `kp` | • Standard | Simple key press, no behavior logic needed. |

### Right Thumb Cluster

| Key (Position) | Function | Behavior | Configuration | Why? |
| :--- | :--- | :--- | :--- | :--- |
| **Inner (Large)** | **Enter** / Layer 4 | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• Term: **175ms**<br>• `quick-tap: 0` | Fast **175ms** for rapid Enter usage. `tap-preferred` + `QT=0` ensures Enter fires instantly like Space. |
| **Middle** | **Space** / Shift | `hold-tap` | • `tap-preferred`<br>• `retro-tap`<br>• Term: **225ms**<br>• `quick-tap: 0` | **The Speed King.** <br>• **225ms:** Extremely forgiving for Space.<br>• **QT=0:** Disables double-tap logic for instant firing.<br>• **Tap-Pref:** Never misses a space during fast typing. |
| **Outer** | **Sym Toggle** | `tap-dance` | • Term: **175ms** | Standard reliable toggle for standard symbol layer access. |

---

## Operational "Feel"

1.  **Typing (Space/Backspace):**
    *   Feels almost indistinguishable from a standard "dumb" keyboard.
    *   Fires instantly (`quick-tap: 0` on Space).
    *   Forgives clumsy/long presses (`retro-tap` + high `tapping-term`).

2.  **Layer Access (Shift/Nav):**
    *   Requires a **deliberate** pause/hold.
    *   You cannot simply "flick" the layer on; you must press-and-hold for a split second (approx 0.2s) to engage the modifier.
