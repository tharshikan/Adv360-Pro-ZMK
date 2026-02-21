# Sunaku's Bilateral Combinations vs. Standard ZMK Hold-Tap (HRM)

## The Core Difference

### Standard ZMK Hold-Tap (Our HRM)
Our standard HRM configuration relies on ZMK's native `behavior-hold-tap` functionality. It uses `hold-trigger-key-positions` to determine whether a held key should act as a modifier or output its base key code.

- **How it works:** When you press and hold a modifier on the left hand, ZMK waits. If you tap a key on the *right* hand, it treats your initial hold as a modifier (Bilateral Combination). If you tap a key on the *left* hand, it assumes you are rolling keys and outputs the literal taps instead of the modifier.
- **The Limitation:** When typing extremely fast, standard ZMK hold-taps can sometimes misjudge overlapping keystrokes. This can lead to accidental modifier activations or dropped characters during rapid, same-hand rolls.

### Sunaku's "Layer Sandwich"
Sunaku's implementation replaces the standard behavior with a robust, procedural "Layer-Sandwich" macro system to guarantee correct output even during incredibly fast or sloppy typing.

- **How it works:** Instead of outputting a modifier upon being held, Sunaku's behavior activates a **hidden, isolated ZMK layer** uniquely assigned to that finger. 
- **Opposite Hand (Modifier):** This hidden layer leaves all opposite-hand keys mapped to `&trans`, allowing the actual modifier underneath to apply normally when chording.
- **Same Hand (Rolling/Cancellation):** The hidden layer maps all *same-hand* keys to a specialized **Tap Macro**. If you hold an HRM key and then tap a key on the same hand, this macro intercepts your action. It forcibly *releases* any active modifiers, explicitly taps the original key you were holding, and then taps the new key you just pressed.
- **The Result:** This approach aggressively prevents false modifier activations on same-hand rolls and ensures modifiers remain "sticky" and robust during cross-hand combinations, without relying entirely on ZMK's dynamic timing engine.

---

## Parameter Comparison

Here is a breakdown of the behavioral parameters defined in our implementation versus Sunaku's default recommendations, as well as the custom settings we chose to use for Sunaku's behavioral engine in our keymap.

### Global Parameters

| Parameter | Our HRM | Sunaku Default | Sunaku (Our Keymap) |
| :--- | :---: | :---: | :---: |
| **flavor** | `tap-preferred` | `tap-preferred` | `tap-preferred` |
| **require-prior-idle-ms** | 180ms | 150ms | 180ms |
| **quick-tap-ms** | 0ms | 200ms | 0ms |
| **hold-trigger-on-release** | Yes | Yes | Yes |
| **retro-tap** | Yes | Yes | Yes |

### Tapping Term Timings (`tapping-term-ms`)

| Finger | Our HRM | Sunaku Default | Sunaku (Our Keymap) |
| :--- | :---: | :---: | :---: |
| **Left Pinky** (`A` / `LGUI`) | 350ms | 280ms | 350ms |
| **Left Ring** (`O` / `Sym 9`) | 270ms | 200ms | 270ms |
| **Left Middle** (`E` / `LShift`) | 270ms | 200ms | 270ms |
| **Left Index** (`I` / `Sym 8`) | 250ms | 200ms | 260ms |
| **Right Index** (`H` / `Sym 8`) | 260ms | 200ms | 260ms |
| **Right Middle** (`T` / `RShift`) | 270ms | 200ms | 270ms |
| **Right Ring** (`N` / `Sym 9`) | 270ms | 200ms | 270ms |
| **Right Pinky** (`S` / `RGUI`) | 350ms | 280ms | 350ms |

*Note: In our compilation of Sunaku's engine, we opted to preserve our original HRM timings to isolate the behavioral differences of the engines, rather than testing both the engine AND Sunaku's faster default timings (`200ms`-`280ms`) simultaneously.*
