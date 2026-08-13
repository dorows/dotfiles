# UFSC VPN Quickshell bar toggle

## Intent

Connect to UFSC's strongSwan VPN from a clickable Omarchy Quickshell widget. A filled accent-colored shield is connected, an outlined shield is disconnected, and clicking toggles the connection.

## Install

Requires NetworkManager, strongSwan, the NetworkManager strongSwan plugin, and `notify-send`. From this feature directory:

```bash
install -Dm700 source/ufsc-vpn-status ~/.config/omarchy/bar/scripts/ufsc-vpn-status
install -Dm700 source/ufsc-vpn-toggle ~/.config/omarchy/bar/scripts/ufsc-vpn-toggle
chmod 700 source/ufsc-vpn-setup
./source/ufsc-vpn-setup
```

Run the setup only when the `UFSC IKEv2` NetworkManager profile does not exist yet. It asks for the IdUFSC username and password, does not echo the password, and saves both in the user-restricted profile; no personal credentials are committed here.

Add this entry beside `omarchy.network` in `bar.layout.right` in `~/.config/omarchy/shell.json`:

```json
{
  "id": "ufsc-vpn",
  "type": "command",
  "exec": "~/.config/omarchy/bar/scripts/ufsc-vpn-status",
  "interval": 2,
  "onClick": "~/.config/omarchy/bar/scripts/ufsc-vpn-toggle",
  "fontSize": 14
}
```

The shell hot-reloads the file. If needed, apply manually with `omarchy restart shell`.
