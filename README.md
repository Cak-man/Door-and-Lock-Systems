# Unity Advanced Door & Lock System

A sophisticated interaction framework for Unity that handles standard doors, locked doors requiring specific items, and complex multi-lock mechanisms.

## ✨ Features
*   **Raycast Interaction:** Precision-based activation using the player's line of sight.
*   **Procedural Door Animation:** Coroutine-based rotation for smooth opening/closing without the need for Animation clips.
*   **Multi-Lock System:** Supports doors that require multiple specific keys or items to unlock, featuring a progress counter (e.g., `1/3`).
*   **Global Inventory Sync:** Integrates with `ItemData` to verify if the player is holding the correct item for specific locks.
*   **Event-Driven:** Includes static C# Actions (`OnAnyDoorOpened`) for easy integration with objective or sound managers.

## 🛠 Components

### 1. Door.cs
The core door logic.
- **Invert Direction:** Toggle between clockwise and counter-clockwise opening.
- **Audio Integration:** Dedicated slots for Open and Close sound effects.
- **Dynamic Tagging:** Switches from `LockedDoor` to `Door` once security criteria are met.

### 2. CameraOpenDoor.cs
The player-side interaction script.
- Detects doors via Raycast.
- Validates held items against the door's required item name (Key-to-Lock matching).

### 3. DoorUnlockSystem.cs
Handles complex puzzles requiring multiple stages to unlock a single door.
- **LockData List:** Define multiple lock objects and their unique required items.
- **Progress UI:** Real-time feedback showing how many locks remain.

## 🕹 Setup Instructions
1. **Standard Door:** Attach `Door` script, set the `Door` tag, and assign audio clips.
2. **Simple Locked Door:** Attach `Door`, set tag to `LockedDoor`. Ensure the object name matches the item name in `ItemData`.
3. **Multi-Lock Puzzle:** 
   - Attach `DoorUnlockSystem` to a manager object.
   - Assign the target door and populate the `Locks` list with the physical lock objects and their corresponding item requirements.

## ⌨️ Controls
| Key | Action |
| :--- | :--- |
| **E** | Interact (Open/Close/Unlock) |

## 📄 Classes Overview
- `Door`: Physical rotation and audio.
- `CameraOpenDoor`: Raycast detection and simple unlocking.
- `DoorUnlockSystem`: Multi-lock logic and progress tracking.
- `ItemData`: Global static storage for the currently held item.
