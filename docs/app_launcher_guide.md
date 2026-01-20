# App Launcher Layer Guide (Layer 7)

The **App Launcher Layer** allows you to open your most frequently used applications instantly using "One-Shot" macros.

## Activation
*   **Key:** `Left Arrow` (Left Hand, Bottom Row, Inner Index/Middle area)
*   **Action:** **Hold** to activate Layer 7. **Tap** for standard Left Arrow.

## Mechanism: "Invisible" Hyper Key
Instead of typing the application name, this layer sends a unique **Hyper Key** combo for instant launching. 

**Trigger:** `Cmd + Opt + Ctrl + Shift` + `[Key]`

## Setup Guide (Required on Mac)
For this to work, you must map these shortcuts on your Mac **once**.

### Method 1: macOS Shortcuts App (Native)
1.  Open **Spotlight** (`Cmd+Space`) and type "Shortcuts".
2.  Open the **Shortcuts** app.
3.  Click **+** (New Shortcut).
4.  Search for action: **"Open App"**. Drag it in.
5.  Click "App" and select **Google Chrome** (or target app).
6.  Click the **(i) Info Icon** in the sidebar.
7.  Click **"Add Keyboard Shortcut"**.
8.  On your ZMK keyboard: Hold **Left Arrow** + Press **H**.
    *   *Mac should detect:* `Cmd + Opt + Ctrl + Shift + H`.
9.  Repeat for other apps.

### Method 2: Raycast / Alfred (Alternative)
If you use these tools, go to "Extensions" or "Hotkeys" and map the same combination.

## Key Mappings

### Left Module (New Additions)
These mappings fill the available keys on the Left Hand, using the mnemonic letters from your Base Layer.

| Key | App | Trigger | Physical Position |
| :--- | :--- | :--- | :--- |
| **P** | Postman | `Hyper + P` | Top Row - Ring |
| **Y** | Spotify | `Hyper + Y` | Top Row - Index |
| **A** | Activity Monitor | `Hyper + A` | Home Row - Pinky |
| **O** | Discord | `Hyper + O` | Home Row - Ring |
| **G** | ChatGPT | `Hyper + G` | Home Row - Inner Index |
| **J** | JetBrains Toolbox | `Hyper + J` | Bottom Row - Ring |

### System Shortcuts (Left Module)
Common OS operations are mapped to intuitive positions on the Left Hand.

| Key | Action | Shortcut | Position |
| :--- | :--- | :--- | :--- |
| **E** | Left Desktop | `Ctrl + Left` | Home Row - Middle |
| **I** | Right Desktop | `Ctrl + Right` | Home Row - Index |
| **Q** | Force Quit | `Cmd + Opt + Esc` | Top Row - Pinky |
| **U** | Mission Control | `Ctrl + Up` | Top Row - Index |
| **X** | Log Off | `Cmd + Shift + Q` | Bottom Row - Pinky |

### Thumb Cluster
| Key | Action | Position |
| :--- | :--- | :--- |
| **Space** | Spotlight (`Cmd + Space`) | Right Thumb (Large Key) |

### Right Module (Primary)

These mappings are aligned with your physical key locations on the **Right Module**.

### Right Hand (Home Row)
| Key | App | Trigger | Physical Position |
| :--- | :--- | :--- | :--- |
| **D** | Slack | `Hyper + D` | Home Row - Inner Index |
| **H** | Chrome | `Hyper + H` | Home Row - Index |
| **T** | WebStorm | `Hyper + T` | Home Row - Middle |
| **N** | Antigravity | `Hyper + N` | Home Row - Ring |
| **S** | Show Desktop | `Hyper + S` | Home Row - Pinky |

### Right Hand (Top Row)
| Key | App | Trigger | Physical Position |
| :--- | :--- | :--- | :--- |
| **F** | Terminal | `Hyper + F` | Top Row - Ring |
| **L** | Zoom | `Hyper + L` | Top Row - Middle |
| **R** | Finder | `Hyper + R` | Top Row - Index |
| **B** | IntelliJ | `Hyper + B` | Top Row - Inner Index |

## Visual Layout (Right Module)

```text
       [F]Term  [L]Zoom  [R]Findr [B]IntellJ
[D]Slk [H]Chrm  [T]WebStm [N]Anti  [S]Dsk
```

## Note on "Antigravity"
Pressing **N** will type "Antigravity" into Spotlight. Ensure this matches your intended app (Google Agent Manager).
