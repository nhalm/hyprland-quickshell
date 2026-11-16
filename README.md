# hyprland-quickshell

A [Quickshell](https://quickshell.org) desktop shell for Hyprland: bar, popups,
quick-settings sidebar, window overview, wallpaper picker and keybind overlay.
Colours come from a [matugen](https://github.com/InioX/matugen) palette.

## Install

```bash
git clone https://github.com/nhalm/hyprland-quickshell ~/.config/quickshell
qs -d
```

Add the palette template to matugen's `config.toml`:

```toml
[templates.quickshell]
input_path = '~/.config/quickshell/matugen/colors.json'
output_path = '~/.local/state/matugen/colors.json'
```

## Develop

In a clone you commit from: `mise trust && mise install && lefthook install`
(`lefthook.yml`: gitleaks on staged changes; versions in `mise.toml`).

## Layout

| Path | What |
|---|---|
| `shell.qml` | Entry point; one bar per screen plus the overlays |
| `bar.json` | Which modules sit left, center and right |
| `modules/` | Bar chips, their popups, and the overlays |
| `components/` | Shared popup building blocks |
| `services/` | Weather and performance data |
| `theme/` | Palette, bar config and wallpaper list |
| `matugen/colors.json` | matugen template for the palette |

## IPC

```bash
qs ipc call overview toggle
qs ipc call wallpaper toggle
qs ipc call sidebar toggle
qs ipc call hotkeys toggle
qs ipc call theme-manager reload
```

## Expects

- `~/.local/state/matugen/colors.json` and `~/.local/state/matugen/mode` (written by matugen)
- `~/.local/scripts/wallpaper.sh` and `~/.local/scripts/theme-mode.sh`, from [nhalm/dotfiles](https://github.com/nhalm/dotfiles)
- Wallpapers in `~/.local/share/wallpapers`
- Hyprland, PipeWire (`wpctl`), NetworkManager, BlueZ, playerctl, swaync, ghostty, btop

## Licence

MIT
