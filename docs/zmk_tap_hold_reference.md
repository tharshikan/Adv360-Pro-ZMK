# ZMK Tap-Hold Configuration Reference

Complete reference for all tap-hold behaviors on the Adv360-Pro, including home row mods and thumb cluster keys. Use this to replicate settings on other firmware (QMK, Vial, etc.).

---

## Design Philosophy

- **Tap-Preferred**: All behaviors prioritize the tap action. Fast typing never accidentally triggers holds.
- **Retro-Tap**: Holding past the tapping term without pressing another key still outputs the tap character — no "dead" keys.
- **Bilateral Enforcement**: Home row mods only activate when the *opposite* hand presses the next key. Prevents same-hand misfires during rolls.
- **Per-Finger Timing**: Slower fingers (pinky) get longer tapping terms; faster fingers (index) get shorter ones.

---

## Home Row Mods — Left Hand

| Key | Tap | Hold | Behavior | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap | Trigger Side |
|:----|:----|:-----|:---------|:-------------|:----------|:-----------|:-------|:----------|:-------------|
| **A** (pinky) | `A` | `LGUI` (Cmd) | `hrm_left_pinky` | 350ms | 200ms | 150ms | tap-preferred | Yes | Right hand only |
| **O** (ring) | `O` | Layer 5 | `hrm_left_ring` | 270ms | 200ms | 150ms | tap-preferred | Yes | Right hand only |
| **E** (middle) | `E` | `LSHIFT` | `hrm_left_middle` | 260ms | 180ms | 150ms | tap-preferred | Yes | Right hand only |
| **I** (index) | `I` | Layer 1 (Sym) | `hrm_left_index` | 260ms | 200ms | 150ms | tap-preferred | Yes | Right hand only |

### Left Hand — Bottom Row

| Key | Tap | Hold | Behavior | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap | Trigger Side |
|:----|:----|:-----|:---------|:-------------|:----------|:-----------|:-------|:----------|:-------------|
| **X** (pinky) | `X` | Layer 2 | `hrm_left_pinky_bottom` | 250ms | 180ms | 150ms | tap-preferred | Yes | Right hand only |
| **J** (ring) | `J` | Layer 11 | `hrm_left_ring_bottom` | 250ms | 180ms | 150ms | tap-preferred | Yes | Right hand only |

---

## Home Row Mods — Right Hand

| Key | Tap | Hold | Behavior | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap | Trigger Side |
|:----|:----|:-----|:---------|:-------------|:----------|:-----------|:-------|:----------|:-------------|
| **H** (index) | `H` | Layer 1 (Sym) | `hrm_right_index` | 220ms | 180ms | 140ms | tap-preferred | Yes | Left hand only |
| **T** (middle) | `T` | `RSHIFT` | `hrm_right_middle` | 230ms | 180ms | 140ms | tap-preferred | Yes | Left hand only |
| **N** (ring) | `N` | Layer 2 | `hrm_right_ring` | 230ms | 180ms | 140ms | tap-preferred | Yes | Left hand only |
| **S** (pinky) | `S` | `RGUI` (Cmd) | `hrm_right_pinky` | 250ms | 180ms | 150ms | tap-preferred | Yes | Left hand only |

### Right Hand — Bottom Row

| Key | Tap | Hold | Behavior | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap | Trigger Side |
|:----|:----|:-----|:---------|:-------------|:----------|:-----------|:-------|:----------|:-------------|
| **V** (ring) | `V` | Layer 11 | `hrm_right_ring_bottom` | 243ms | 180ms | 150ms | tap-preferred | Yes | Left hand only |
| **DOT** (pinky) | `.` | Layer 5 | `hrm_right_pinky_bottom` | 243ms | 180ms | 150ms | tap-preferred | Yes | Left hand only |

---

## Per-Finger Timing Summary

| Finger | Left Tapping Term | Right Tapping Term | Quick Tap | Prior Idle |
|:-------|:------------------|:-------------------|:----------|:-----------|
| Pinky | 350ms | 250ms | 180–200ms | 150ms |
| Ring | 270ms | 230ms | 180–200ms | 140-150ms |
| Middle | 260ms | 230ms | 180ms | 140-150ms |
| Index | 260ms | 220ms | 180–200ms | 140-150ms |

> Left pinky has the highest tapping term (350ms) because it doubles as the GUI/Cmd key, which is easy to misfire on the weakest finger.

---

## Thumb Cluster

| Position | Tap | Hold | Behavior | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap |
|:---------|:----|:-----|:---------|:-------------|:----------|:-----------|:-------|:----------|
| **Left Outer (Large)** | `Backspace` | Layer 4 (Nav) | `smart_bspc2` → `bs_nav` | 220ms | 175ms | 160ms | tap-preferred | Yes |
| **Left Inner (Large)** | `Escape` | `LCTRL` | `mt_ctrl_esc` | 220ms | 0ms | 140ms | tap-preferred | Yes |
| **Left Small Bottom** | `Escape` | `LALT` (Option) | `mt_opt_esc` | 200ms | 0ms | 140ms | tap-preferred | Yes |
| **Left Cmd+C** | `Cmd+C` | Layer 9 (Launcher) | `lt_launcher` | 220ms | 0ms | 180ms | tap-preferred | Yes |
| **Right Inner (Large)** | `Enter` | `RCTRL` | `mt_ctrl_enter` | 175ms | 0ms | — | tap-preferred | Yes |
| **Right Outer (Large)** | `Space` | Layer 3 (Nav) | `sp_nav` | 190ms | 0ms | 140ms | tap-preferred | Yes |
| **Right Small Bottom** | `Tab` | `LALT` (Option) | `mt_opt_tab` | 200ms | 0ms | 140ms | tap-preferred | Yes |

### Thumb Key Notes

- **Backspace** (`smart_bspc2`): A modifier-morph — tapping gives Backspace, holding gives Layer 4. With Shift held, it sends `Option+Backspace` (delete word).
- **Space**: `quick-tap: 0` disables double-tap repeat logic so Space fires instantly every time.
- **Enter**: Shortest tapping term (175ms) for rapid Enter usage.
- **Sticky Nav** (`sl 4`): Tap once to activate Layer 4 for one keypress; hold for momentary layer.

---

## Other Hold-Tap Behaviors (Unused/Alternate)

These are defined in the keymap but may be used on non-base layers or as alternates:

| Behavior | Tap | Hold | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap |
|:---------|:----|:-----|:-------------|:----------|:-----------|:-------|:----------|
| `enter_cmd` | `Enter` | `LGUI` (Cmd) | 200ms | 175ms | — | balanced | No |
| `bs_shift` | `Backspace` | `LSHIFT` | 220ms | 175ms | 160ms | tap-preferred | Yes |
| `sp_shift` | `Space` | `LSHIFT` | 220ms | 0ms | 140ms | tap-preferred | Yes |

---

## Complete Key Config Table (All Tap-Hold Keys)

| # | Key | Finger | Hand | Tap Output | Hold Output | Tapping Term | Quick Tap | Prior Idle | Flavor | Retro Tap | Bilateral |
|:--|:----|:-------|:-----|:-----------|:------------|:-------------|:----------|:-----------|:-------|:----------|:----------|
| 1 | A | Pinky | Left | `A` | `LGUI` | 350ms | 200ms | 150ms | tap-pref | Yes | Yes (R) |
| 2 | O | Ring | Left | `O` | Layer 5 | 270ms | 200ms | 150ms | tap-pref | Yes | Yes (R) |
| 3 | E | Middle | Left | `E` | `LSHIFT` | 260ms | 180ms | 150ms | tap-pref | Yes | Yes (R) |
| 4 | I | Index | Left | `I` | Layer 1 | 260ms | 200ms | 150ms | tap-pref | Yes | Yes (R) |
| 5 | X | Pinky | Left | `X` | Layer 2 | 250ms | 180ms | 150ms | tap-pref | Yes | Yes (R) |
| 6 | J | Ring | Left | `J` | Layer 11 | 250ms | 180ms | 150ms | tap-pref | Yes | Yes (R) |
| 7 | H | Index | Right | `H` | Layer 1 | 220ms | 180ms | 140ms | tap-pref | Yes | Yes (L) |
| 8 | T | Middle | Right | `T` | `RSHIFT` | 230ms | 180ms | 140ms | tap-pref | Yes | Yes (L) |
| 9 | N | Ring | Right | `N` | Layer 2 | 230ms | 180ms | 140ms | tap-pref | Yes | Yes (L) |
| 10 | S | Pinky | Right | `S` | `RGUI` | 250ms | 180ms | 150ms | tap-pref | Yes | Yes (L) |
| 11 | V | Ring | Right | `V` | Layer 11 | 243ms | 180ms | 150ms | tap-pref | Yes | Yes (L) |
| 12 | DOT | Pinky | Right | `.` | Layer 5 | 243ms | 180ms | 150ms | tap-pref | Yes | Yes (L) |
| 13 | BSPC | Thumb | Left | `Backspace` | Layer 4 | 220ms | 175ms | 160ms | tap-pref | Yes | No |
| 14 | ESC | Thumb | Left | `Escape` | `LCTRL` | 220ms | 0ms | 140ms | tap-pref | Yes | No |
| 15 | ESC2 | Thumb | Left | `Escape` | `LALT` | 200ms | 0ms | 140ms | tap-pref | Yes | No |
| 16 | Enter | Thumb | Right | `Enter` | `RCTRL` | 175ms | 0ms | — | tap-pref | Yes | No |
| 17 | Space | Thumb | Right | `Space` | Layer 3 | 190ms | 0ms | 140ms | tap-pref | Yes | No |
| 18 | TAB | Thumb | Right | `Tab` | `LALT` | 200ms | 0ms | 140ms | tap-pref | Yes | No |
