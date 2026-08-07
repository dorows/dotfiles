# UFSC VPN Waybar toggle

## Intent

Connect to UFSC's strongSwan VPN from a clickable Waybar lock. The bright lock is connected, the dim lock is disconnected, and clicking toggles the connection.

## Install

Requires NetworkManager, strongSwan, the NetworkManager strongSwan plugin, `jq`, and `notify-send`. From this feature directory:

```bash
install -Dm700 source/ufsc-vpn-status ~/.config/waybar/scripts/ufsc-vpn-status
install -Dm700 source/ufsc-vpn-toggle ~/.config/waybar/scripts/ufsc-vpn-toggle
chmod 700 source/ufsc-vpn-setup
./source/ufsc-vpn-setup
```

The setup asks the user for their IdUFSC username and password. It does not echo the password and saves both in the user-restricted NetworkManager profile; no personal credentials are committed here.

Add `"custom/ufsc-vpn"` beside `"network"` in `modules-right` in `~/.config/waybar/config.jsonc`, then add:

```jsonc
"custom/ufsc-vpn": {
  "exec": "$HOME/.config/waybar/scripts/ufsc-vpn-status",
  "return-type": "json",
  "interval": 5,
  "signal": 11,
  "on-click": "$HOME/.config/waybar/scripts/ufsc-vpn-toggle",
  "tooltip": true
},
```

Add to `~/.config/waybar/style.css`:

```css
#custom-ufsc-vpn {
  min-width: 12px;
  margin-right: 13px;
}

#custom-ufsc-vpn.disconnected {
  opacity: 0.45;
}
```

Apply with `jq empty ~/.config/waybar/config.jsonc && omarchy restart waybar`.
