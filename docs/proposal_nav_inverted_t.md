# Proposal: "Inverted-T" (Gamer Style) Nav Layer

## The Concept
Shift the Right Hand Arrow Cluster from the current **Linear (VIM)** style to a **Triangular (Inverted-T)** style, similar to WASD or standard keyboard arrow clusters. This leverages the strong middle finger for vertical movement and unloads the pinky.

## Proposed Mapping (Right Hand)

| Finger | Physical Key | Current Function | **Proposed Function** |
| :--- | :--- | :--- | :--- |
| **Index** | **H** | Left Arrow | **Left Arrow** |
| **Middle** | **T** | Down Arrow | **Down Arrow** |
| **Ring** | **N** | Up Arrow | **Right Arrow** |
| **Pinky** | **S** | Right Arrow | **Cmd+T (New Tab)** |
| **Middle (Top)** | **L** | Cmd+T | **Up Arrow** |

## Ergonomic Benefits

### 1. Stronger Fingers
It moves **Right Arrow** (a very common key) from your weak **Pinky** to your strong **Ring Finger**. The pinky is relegated to "New Tab" (Cmd+T), which is a lower-frequency, "one-shot" action ideal for that finger.

### 2. Vertical Intuition
Using your **Middle Finger** for both **Up** (Top Row) and **Down** (Home Row) creates a natural vertical column. It mimics the "W/S" movement pattern familiar to gamers (WASD) and standard inverted-T users.

### 3. Spatial Mental Model
It creates a spatial "Triangle" that maps perfectly to 2D navigation (Up is physically above Down), reducing cognitive load compared to a linear row.

## Visual Layout

```
    [ L ] (UP)
      ^
      |
[ H ] [ T ] [ N ]
(LFT) (DWN) (RGT)

      [ S ] -> Cmd+T (New Tab)
```

## Status
*   **Drafted:** 2026-01-21
*   **Status:** Proposal Only (Not Implemented)
