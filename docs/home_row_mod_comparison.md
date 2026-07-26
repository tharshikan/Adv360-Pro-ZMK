# Home Row Mod Comparison Report

Three base layers, each wired to its own family of hold-tap behaviors:

| Layer | Behavior prefix | Design philosophy |
|---|---|---|
| **Base_urob** | `urob_*` | `balanced` flavor, **positional** (`hold-trigger-on-release`), long anchor timings on left hand |
| **base_tharshi_tap_preffered** | `hrm_*` | `tap-preferred` + `retro-tap`, positional, tight/fast timings |
| **sunaku_base** | `sunaku_*` | `tap-preferred` + `retro-tap`, **no** hold-trigger-on-release, uniform timings, high quick-tap |

All timings in **ms**. Columns: **TT** = tapping-term-ms · **QT** = quick-tap-ms · **RPI** = require-prior-idle-ms · **HTR** = hold-trigger-on-release · **HTKP** = hold-trigger-key-positions.

---

## 1. Base_urob (`urob_*`)

| Position | Mod | TT | QT | RPI | Flavor | retro-tap | HTR | HTKP |
|---|---|---|---|---|---|---|---|---|
| L pinky | LGUI | 350 | 150 | 150 | tap-preferred | – | ✅ | KEYS_R + THUMBS |
| L ring | (layer 9) | **500** | 150 | **230** | balanced | – | ✅ | KEYS_R + THUMBS |
| L middle | LSHFT | 370 | 150 | 230 | balanced | – | ✅ | KEYS_R + THUMBS |
| L index | (layer 5) | 390 | 150 | 70 | balanced | – | ✅ | H/T only (41, 42) |
| R index | (layer 5) | 280 | 150 | 70 | balanced | – | ❌ | KEYS_L + THUMBS |
| R middle | RSHFT | 280 | 150 | 70 | balanced | – | ✅ | KEYS_L + THUMBS |
| R ring | (layer 6) | 280 | 150 | 70 | balanced | – | ❌ | KEYS_L + THUMBS |
| R pinky | RGUI | 280 | 150 | 70 | balanced | – | ✅ | KEYS_L + THUMBS |
| L pinky-bottom | (layer 6) | 280 | 150 | 150 | balanced | – | ✅ | KEYS_R + THUMBS |
| L ring-bottom | (layer 4) | 280 | 150 | 150 | balanced | – | ✅ | KEYS_R + THUMBS |
| R ring-bottom | (layer 4) | 280 | 150 | 70 | balanced | – | ✅ | KEYS_L + THUMBS |
| R pinky-bottom | (layer 9) | 280 | 150 | 70 | balanced | – | ✅ | KEYS_L + THUMBS |

**Notes:** No `retro-tap` anywhere. Left-hand anchors are deliberately slow/deliberate (ring 500/230, index 390/70, middle 370/230, pinky 350). The left index can resolve early only for H/T, which output `(`/`)` on Layer 5; every other symbol requires the full 390ms hold. Right-hand behaviors use 280/150/70; the remaining bottom-left behaviors use 280/150/150. ⚠️ **R index and R ring are missing `hold-trigger-on-release`** — likely inconsistencies vs. the rest of the family.

### Base_urob — Thumb cluster (space / enter / backspace / esc)

| Key | Behavior | Hold | Tap | TT | QT | RPI | Flavor | retro-tap | HTR/HTKP | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| **Space** | `sp_nav` | Layer 7 (Nav) | SPACE | 200 | 175 | 150 | balanced | – | – | – |
| **Enter** | `mt_ctrl_enter` | RCTRL | ENTER | 175 | 0 | – | tap-preferred | ✅ | – | No require-prior-idle; QT=0 |
| **Backspace** | `smart_bspc2` → `bs_nav` | Layer 8 | BSPC | 220 | 175 | 160 | tap-preferred | ✅ | – | Mod-morph: with Shift held → `⌥⌫` (delete word) |
| **Esc** | `mt_ctrl_esc` | LCTRL | ESCAPE | 220 | 0 | 140 | tap-preferred | ✅ | – | QT=0 |

**Notes:** None of the thumb keys are positional (`hold-trigger-key-positions`) — they trigger by timing alone. Space is the only one using `balanced`; the other three are `tap-preferred` + `retro-tap`. `Enter` and `Esc` use `quick-tap-ms = 0` (no quick-tap repeat). `Backspace` is a mod-morph wrapping `bs_nav`, so an unshifted hold enters the Nav layer (8) while a shifted tap deletes the previous word.

---

## 2. base_tharshi_tap_preffered (`hrm_*`)

| Position | Mod | TT | QT | RPI | Flavor | retro-tap | HTR | HTKP |
|---|---|---|---|---|---|---|---|---|
| L pinky | LGUI | 350 | 200 | 150 | tap-preferred | ✅ | ✅ | KEYS_R |
| L ring | (layer 9) | 270 | 200 | 150 | tap-preferred | ✅ | ✅ | KEYS_R |
| L middle | LSHFT | 260 | 180 | 150 | tap-preferred | ✅ | ✅ | KEYS_R |
| L index | (layer 5) | 260 | 200 | 150 | tap-preferred | ✅ | ✅ | KEYS_R |
| R index | (layer 5) | 220 | 180 | 140 | tap-preferred | ✅ | ✅ | KEYS_L |
| R middle | RSHFT | 230 | 180 | 140 | tap-preferred | ✅ | ✅ | KEYS_L |
| R ring | (layer 6) | 230 | 180 | 140 | tap-preferred | ✅ | ✅ | KEYS_L |
| R pinky | RGUI | 250 | 180 | 150 | tap-preferred | ✅ | ✅ | KEYS_L |
| L pinky-bottom | (layer 6) | 250 | 180 | 150 | tap-preferred | ✅ | ✅ | KEYS_R |
| L ring-bottom | (layer 4) | 250 | 180 | 150 | tap-preferred | ✅ | ✅ | KEYS_R |
| R ring-bottom | (layer 4) | 243 | 180 | 150 | tap-preferred | ✅ | ✅ | KEYS_L |
| R pinky-bottom | (layer 9) | 243 | 180 | 150 | tap-preferred | ✅ | ✅ | KEYS_L |

**Notes:** Fully consistent — every key is `tap-preferred` + `retro-tap` + positional (`HTR`). Fastest of the three (TT 220–350). Right hand tuned faster (220–250) than left (260–350). Note HTKP uses **only** `KEYS_R`/`KEYS_L` (no `THUMBS`), unlike urob/sunaku.

---

## 3. sunaku_base (`sunaku_*`)

| Position | Mod | TT | QT | RPI | Flavor | retro-tap | HTR | HTKP |
|---|---|---|---|---|---|---|---|---|
| L pinky | LGUI | 270 | 300 | 230 | tap-preferred | ✅ | ❌ | KEYS_R + THUMBS |
| L ring | (layer 9) | 270 | 300 | 230 | tap-preferred | ✅ | ❌ | KEYS_R + THUMBS |
| L middle | LSHFT | 270 | 300 | 230 | tap-preferred | ✅ | ❌ | KEYS_R + THUMBS |
| L index | (layer 5) | 270 | 300 | 230 | tap-preferred | ✅ | ❌ | KEYS_R + THUMBS |
| R index | (layer 5) | 200 | 300 | 70 | tap-preferred | ✅ | ❌ | KEYS_L + THUMBS |
| R middle | RSHFT | 200 | 300 | 70 | tap-preferred | ✅ | ❌ | KEYS_L + THUMBS |
| R ring | (layer 6) | 200 | 300 | 70 | tap-preferred | ✅ | ❌ | KEYS_L + THUMBS |
| R pinky | RGUI | 200 | **200** | 70 | tap-preferred | ✅ | ❌ | KEYS_L + THUMBS |
| L pinky-bottom | (layer 6) | 270 | 300 | 230 | tap-preferred | ✅ | ❌ | KEYS_R + THUMBS |
| L ring-bottom | (layer 4) | 270 | 300 | 230 | tap-preferred | ✅ | ❌ | KEYS_R + THUMBS |
| R ring-bottom | (layer 4) | 200 | 300 | 70 | tap-preferred | ✅ | ❌ | KEYS_L + THUMBS |
| R pinky-bottom | (layer 9) | 200 | 300 | 70 | tap-preferred | ✅ | ❌ | KEYS_L + THUMBS |

**Notes:** Cleanly split by hand — **left = 270/300/230**, **right = 200/300/70** (only exception: R pinky QT=200). Highest quick-tap (300) of all three and lowest right-hand RPI (70). **No `hold-trigger-on-release`** on any key — it relies on `hold-trigger-key-positions` alone.

---

## Cross-Config Summary

| Dimension | Base_urob | base_tharshi | sunaku_base |
|---|---|---|---|
| **Flavor** | balanced (pinky = tap-pref) | tap-preferred | tap-preferred |
| **retro-tap** | ❌ none | ✅ all | ✅ all |
| **hold-trigger-on-release** | ✅ most (2 missing) | ✅ all | ❌ none |
| **THUMBS in trigger set** | All except L index | ❌ never | ✅ always |
| **Tapping-term range** | 280–500 (slow anchors) | 220–350 (fast) | 200 (R) / 270 (L) |
| **Quick-tap** | 150 uniform | 180–200 | 300 (200 R-pinky) |
| **Require-prior-idle** | 70–230 | 140–150 | 70 (R) / 230 (L) |
| **Feel** | Deliberate, hard to misfire; slow left anchors | Fast & responsive, retro-tap safety net | Very fast right hand, generous quick-tap for rolls |

**Key takeaways:**

- **urob** is the most conservative (balanced flavor, no retro-tap, deliberate left-hand anchors up to 500ms) — biased against accidental mod activation but slower to trigger.
- **tharshi** is the fastest and most internally consistent — tap-preferred + retro-tap everywhere, tight sub-350ms terms.
- **sunaku** trades away `hold-trigger-on-release` for a very high quick-tap (300ms) and an aggressively fast right hand (RPI 70) — optimized for fast typing rolls, leaning on positional triggering alone.

> ⚠️ In **Base_urob**, `urob_right_index` and `urob_right_ring` lack `hold-trigger-on-release` while their siblings have it — probably unintentional.
