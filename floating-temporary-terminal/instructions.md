# Floating temporary terminal

## Intent

Open an interactive terminal above tiled windows with `Super + Shift + Enter`. It closes when the shell exits.

## Install

Replace the existing `Super + Shift + Enter` binding in `~/.config/hypr/bindings.conf` with:

```ini
bindd = SUPER SHIFT, RETURN, Floating terminal, exec, uwsm-app -- xdg-terminal-exec --app-id=org.omarchy.terminal
```

The `org.omarchy.terminal` app ID matches Omarchy's existing rule, which floats, centers, and sizes the terminal at 875×600. Reload and verify Hyprland:

```bash
hyprctl reload
hyprctl configerrors
```
