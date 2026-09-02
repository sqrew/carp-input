# carp-input

A semantic, action-based input management library for the [Carp](https://github.com/carp-lang/Carp) programming language.

This library decouples raw hardware events (keys, mouse buttons, joystick axes) from game logic. Instead of checking if the "W" key is pressed, your game logic asks if the `"MoveForward"` action is active.

## Features
- **Semantic Mapping**: Map multiple raw inputs to a single named action.
- **Aggregation**: Automatically handles multiple bindings for the same action (e.g., Spacebar OR Gamepad A for `"Jump"`).
- **Analog & Digital**: Supports binary buttons, analog axes, and mouse deltas.
- **Easy Rebinding**: Update controls at runtime by modifying the binding list.

## Installation

```
(load "git@github.com:carpentry-org/carp-input@master")
```

That includes the GLFW backend, which needs `glfw3` visible to `pkg-config`.
For the manager alone, with no window-library dependency:

```
(load "git@github.com:carpentry-org/carp-input@master" "input.carp")
```

## Examples

See [examples.md](examples.md) for usage examples, and the
[API documentation](https://carpentry.dev/carp-input) for the full reference.

## License
MIT
