# carp-input

A semantic, action-based input management library for the [Carp](https://github.com/carp-lang/Carp) programming language.

This library decouples raw hardware events (keys, mouse buttons, joystick axes) from game logic. Instead of checking if the "W" key is pressed, your game logic asks if the `"MoveForward"` action is active.

## Features
- **Semantic Mapping**: Map multiple raw inputs to a single named action.
- **Aggregation**: Automatically handles multiple bindings for the same action (e.g., Spacebar OR Gamepad A for `"Jump"`).
- **Analog & Digital**: Supports binary buttons, analog axes, and mouse deltas.
- **Easy Rebinding**: Update controls at runtime by modifying the binding list.

## Usage

```carp
(load "carp-input/input.carp")
(use InputManager)

(defn main []
  (let [mgr (InputManager.create win)]
    (do
      ;; 1. Define bindings
      (InputManager.add-binding! &mgr "Jump" (InputSource.Key GLFW.Keycode.Space) 1.0)
      (InputManager.add-binding! &mgr "Jump" (InputSource.MouseButton GLFW.MouseButton.Left) 1.0)
      (InputManager.add-binding! &mgr "LookX" (InputSource.MouseDeltaX) 0.1)

      ;; 2. Update every frame
      (InputManager.update! &mgr)

      ;; 3. Query actions semantically
      (if (InputManager.action-digital? &mgr "Jump")
          (println "Jumping!")
          ())
      
      (let [look-x (InputManager.action-analog &mgr "LookX")]
          (camera-rotate! look-x)))))
```

## License
MIT
