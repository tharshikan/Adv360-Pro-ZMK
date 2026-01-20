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

## Key Mappings (Right Module Focused)

These mappings are aligned with your physical key locations on the **Right Module**.

### Right Hand (Home Row)
| Key | App | Physical Position |
| :--- | :--- | :--- |
| **D** | Show Desktop | Home Row - Inner Index |
| **H** | Chrome | Home Row - Index |
| **T** | WebStorm | Home Row - Middle |
| **N** | Antigravity | Home Row - Ring |
| **S** | Slack | Home Row - Pinky |

### Right Hand (Top Row)
| Key | App | Physical Position |
| :--- | :--- | :--- |
| **F** | Terminal | Top Row - Ring |
| **L** | Zoom | Top Row - Middle |
| **R** | Finder | Top Row - Index |
| **B** | IntelliJ | Top Row - Inner Index |

## Visual Layout (Right Module)

```text
       [F]Term  [L]Zoom  [R]Findr [B]IntellJ
[D]Dsk [H]Chrm  [T]WebStm [N]Anti  [S]Slack
```

## Note on "Antigravity"
Pressing **N** will type "Antigravity" into Spotlight. Ensure this matches your intended app (Google Agent Manager).
