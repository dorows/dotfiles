# Borderless single window

## Intent

Hide the active border when a workspace has only one visible tiled window. The normal border returns automatically when another tiled window opens; floating windows keep their borders.

## Install

Add this to `~/.config/hypr/looknfeel.lua`:

```lua
hl.window_rule({
  match = { float = false, workspace = "w[tv1]" },
  border_size = 0,
})
```

Reload and verify Hyprland:

```bash
hyprctl reload
hyprctl configerrors
```
