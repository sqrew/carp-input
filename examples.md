# Examples

## Basic Usage

Mapping raw keys and mouse actions to semantic game actions, updating the manager, and querying them digitally or analogically:

```clojure
(load "git@github.com:carpentry-org/carp-input@master" "input.carp")
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
