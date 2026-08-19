# Floating ZapZap window

## Intent

Keep ZapZap running in the tray, but reveal it above tiled windows as a centered 1200×800 landscape window with focus.

## Install

Keep **Start in background** enabled in ZapZap. Add this personal window rule to `~/.config/hypr/hyprland.lua` after the Omarchy defaults are loaded:

```lua
o.window("^com\\.rtosta\\.zapzap$", {
  float = true,
  center = true,
  size = { 1200, 800 },
  focus_on_activate = true,
})
```

Reload and verify Hyprland:

```bash
hyprctl reload
hyprctl configerrors
```
