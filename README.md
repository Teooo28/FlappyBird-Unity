# Flappy Bird Clone - Unity 2D

A 2D arcade game inspired by the classic Flappy Bird, developed using the Unity Engine and C#. This project demonstrates fundamental game development mechanics, including physics-based movement, dynamic object spawning, collision detection, and UI state management.

---

## 🎮 How to Play

*   **Jump/Flap:** Press the `Space` bar to make the bird flap and gain altitude.
*   **Objective:** Navigate through the gaps in the moving pipes. Timing is crucial!
*   **Scoring:** Each time you successfully pass through a pair of pipes, you earn 1 point.
*   **Game Over:** Hitting the ground or colliding with a pipe ends the run.

---

## 🚀 Key Features

*   **Physics-Based Movement:** The player controls the bird using the `Space` key, which applies an upward velocity directly to the `Rigidbody2D` component.
*   **Dynamic Obstacle Generation:** Pipes are automatically instantiated at a defined `spawnRate` using a timer, with randomized vertical positions based on a calculated `heightOffset`.
*   **Memory Optimization:** Pipes translate continuously to the left using `Time.deltaTime`. Once they pass a specific `deadZone` coordinate off-screen, they are automatically destroyed (`Destroy(gameObject)`) to free up system memory.
*   **Precise Scoring System:** Implements a specific trigger zone between pipes that verifies the player's layer (`layer == 3`) before communicating with the Logic Manager to increment the score.
*   **Game State & UI Management:** A dedicated Logic Manager handles real-time score increments, triggers the Game Over screen upon collision, and manages scene reloading for quick restarts.

---

## 🛠️ Technology Stack

*   **Game Engine:** Unity 2D
*   **Programming Language:** C#
*   **Core Concepts Used:** `Rigidbody2D`, `Collision2D`, `SceneManager`, `Time.deltaTime`, Layer-based Collision, Prefab Instantiation & Destruction

---

## 💻 Code Structure

The game's logic is modularized into dedicated C# scripts:
*   **`BirdScript.cs`:** Manages the player's flap mechanics, velocity, and detects physical collisions with obstacles to trigger the game-over state.
*   **`LogicScript.cs`:** Controls the UI elements (`scoreText`, `gameOverScreen`), safely updates the player's score, and handles scene management (`SceneManager.LoadScene`) for restarting the game.
*   **`PipeSpawnScript.cs`:** Acts as the game's director for obstacles, keeping track of time and instantiating new pipe prefabs at random heights.
*   **`PipeMoveScript.cs`:** Attached to each pipe prefab, giving it constant leftward movement and self-destructing once it safely leaves the camera's view.
*   **`PipeMiddleScript.cs`:** Placed in the gap between pipes. Uses `OnTriggerEnter2D` to detect when the bird (specifically filtered by collision layer 3) safely passes through, securely communicating with the `LogicScript` to add to the player's score.

---

## ⚙️ How to Run Locally

1.  Clone this repository.
2.  Open **Unity Hub** and click **Add project from disk**.
3.  Select the cloned folder.
4.  Once the project opens, navigate to the `Assets/Scenes` folder and double-click `SampleScene` to load it.
5.  Press the **Play** button at the top of the Unity Editor to test the game.
