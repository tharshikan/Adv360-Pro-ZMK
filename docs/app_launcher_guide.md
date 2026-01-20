# App Launcher Layer Guide (Layer 7)

The **App Launcher Layer** allows you to open your most frequently used applications instantly using "One-Shot" macros.

## Activation
*   **Key:** `Left Arrow` (Left Hand, Bottom Row, Inner Index/Middle area)
*   **Action:** **Hold** to activate Layer 7. **Tap** for standard Left Arrow.

## Mechanism
This layer uses **ZMK Macros** to:
1.  Trigger Spotlight (`Cmd + Space`).
2.  Wait briefly (`50ms`).
3.  Type the Application Name.
4.  Press `Enter`.

## Key Mappings

### Left Hand (Primary)
| Key | App | Mnemonic |
| :--- | :--- | :--- |
| **B** | Chrome | **B**rowser |
| **W** | WebStorm | **W**ebStorm |
| **S** | Slack | **S**lack |
| **A** | Antigravity | **A**ntigravity |
| **M** | Agent Manager | **M**anager |
| **N** | Notes | **N**otes |
| **D** | Show Desktop | **D**esktop (`F11`) |
| **O** | SourceTree | s**O**urce |
| **Z** | Zoom | **Z**oom |
| **F** | Finder | **F**inder |
| **G** | Ghostty | **G**hostty |
| **T** | Terminal | **T**erminal |

### Right Hand (Secondary)
| Key | App | Mnemonic |
| :--- | :--- | :--- |
| **Y** | System Settings | s**Y**stem |

## Visual Layout

```text
(Hold Left Arrow)

Top Row:    (Standard)    [W]ebstm (Standard)      (Standard)      [T]erminal   
Home Row:   [A]ntigrav    [S]lack  [D]esktop       [F]inder        [G]hostty 
Bottom Row: [Z]oom        (Standard) (Standard)    (Standard)      [B]rowser 

Right Hand:
[N]otes  [M]anagr  [O]srcTree  [Y]SysSet
```
