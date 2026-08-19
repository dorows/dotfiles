# Super+Tab recent window cycling

## Intent

Use `Super + Tab` to cycle through recently focused windows instead of switching to the next workspace.

## Install

Add this to `~/.config/hypr/bindings.lua`:

```lua
hl.unbind("SUPER + TAB")
o.bind("SUPER + TAB", "Focus on next recent window", hl.dsp.window.cycle_next())
o.bind("SUPER + TAB", "Reveal active window on top", hl.dsp.window.bring_to_top())
```

The user binding file loads after Omarchy's packaged defaults, so this override survives updates. Reload and verify Hyprland:

```bash
hyprctl reload
hyprctl configerrors
```
