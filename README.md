# niriha

A personal Quickshell setup for the Niri Wayland compositor.
Minimal, fast, Gruvbox only for now.

> [!WARNING]
> Built for a specific machine and workflow. Use it as a reference.

## Screenshots

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/4b2b9e1d-b28e-4f67-b19f-11eb0724810f" /></td>
    <td><img src="https://github.com/user-attachments/assets/21a9844e-98c5-4016-9c62-ee015559af9d" /></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/0c1fb403-99ca-4aeb-9f32-e644ae9e0e36" /></td>
    <td><img src="https://github.com/user-attachments/assets/989865a8-a058-4cc7-9724-b404392e5080" /></td>
  </tr>
</table>

## Features and Dependencies

<table>
  <tr>
    <th width="50%">Features</th>
    <th width="50%">Dependencies</th>
  </tr>
  <tr>
    <td valign="top">
      <ul>
        <li><b>Status bar</b>: workspaces, clock, quick controls. Right-click opens Control Center</li>
        <li><b>Workspace layout</b>: overview of all Niri workspaces</li>
        <li><b>Launcher</b>: keyboard-driven app search</li>
        <li><b>Wallpaper picker</b>: reads <code>~/Wallpapers/</code>, applies with swww</li>
        <li><b>Status monitor</b>: CPU, RAM, temperature from <code>/proc</code></li>
        <li><b>Calendar</b>: toggleable popup</li>
        <li><b>Control Center</b>: volume, brightness, network, Bluetooth, power profile, media</li>
      </ul>
    </td>
    <td valign="top">
      <ul>
        <li><code>quickshell</code>: shell framework</li>
        <li><code>niri</code>: compositor</li>
        <li><code>swww</code>: wallpapers</li>
        <li><code>pipewire</code> <code>wireplumber</code>: audio</li>
        <li><code>brightnessctl</code>: brightness</li>
        <li><code>playerctl</code>: media</li>
        <li><code>networkmanager</code>: WiFi</li>
        <li><code>bluez</code>: Bluetooth</li>
        <li><code>power-profiles-daemon</code>: power profiles</li>
        <li><code>qt6-svg</code> <code>qt6-imageformats</code>: icons</li>
        <li><code>imagemagick</code>: image processing</li>
        <li><code>foot</code>: terminal</li>
      </ul>
    </td>
  </tr>
</table>

## Installation

<table>
  <tr>
    <th width="33%">1. Dependencies</th>
    <th width="33%">2. Copy configs</th>
    <th width="33%">3. Run</th>
  </tr>
  <tr>
    <td valign="top">
      Install the packages above, the <a href="https://fonts.google.com/specimen/Google+Sans">Google Sans</a> font, and an icon theme such as <a href="https://github.com/PapirusDevelopmentTeam/papirus-icon-theme">Papirus</a>.
      <br/><br/>
      Set it at the top of <code>shell.qml</code>:
      <br/>
      <code>//@ pragma IconTheme Papirus</code>
    </td>
    <td valign="top">
      This overwrites your Niri and Foot configs. Back them up first.
      <br/><br/>
      <code>git clone https://github.com/yourusername/niriha</code>
      <br/>
      <code>cp -r niriha/.config/* ~/.config/</code>
    </td>
    <td valign="top">
      <code>quickshell -c niriha</code>
      <br/><br/>
      Autostart in <code>~/.config/niri/config.kdl</code>:
      <br/>
      <code>spawn-at-startup "quickshell" "-c" "niriha"</code>
    </td>
  </tr>
</table>

## Keybinds and Planned

<table>
  <tr>
    <th width="50%">Keybinds</th>
    <th width="50%">Planned</th>
  </tr>
  <tr>
    <td valign="top">
      <ul>
        <li><code>Mod+Space</code>: Launcher</li>
        <li><code>Mod+C</code>: Control Center</li>
        <li><code>Mod+W</code>: Wallpaper picker</li>
        <li><code>Mod+A</code>: Calendar</li>
        <li><code>Mod+S</code>: System stats</li>
      </ul>
    </td>
    <td valign="top">
      <ul>
        <li>Power menu</li>
        <li>Shaders</li>
        <li>Wifi and Bluetooth panel</li>
        <li>Lockscreen</li>
        <li>File search and emoji picker</li>
        <li>Clipboard viewer</li>
        <li>Multi-theme support</li>
      </ul>
    </td>
  </tr>
</table>

Already set in the included `config.kdl`. For your own config, add:

```kdl
binds {
    Mod+Space { spawn "sh" "-c" "qs ipc -c niriha call launcher toggle"; }
    Mod+C     { spawn "sh" "-c" "qs ipc -c niriha call controlcenter toggle"; }
    Mod+W     { spawn "sh" "-c" "qs ipc -c niriha call wallpaper toggle"; }
    Mod+A     { spawn "sh" "-c" "qs ipc -c niriha call calendar toggle"; }
    Mod+S     { spawn "sh" "-c" "qs ipc -c niriha call stats toggle"; }
}
```

## Notes

| Topic | Detail |
|---|---|
| Resolution | Tested at 1080p. Adjust margins in `ActionBar.qml` for others |
| Bar space | Add `struts { top 30; }` to your Niri config |
| Wallpapers | Put them in `~/Wallpapers/` |
| Media card | Shows only while an MPRIS player is running |

## FAQ

<details>
<summary>Why Quickshell?</summary>

Around 150kb total, no plugin manager, no daemon.
</details>

<details>
<summary>Why no theming yet?</summary>

matugen, HeroUI, and pywal were not accurate enough. A custom theming layer is planned.
</details>

<details>
<summary>Why is the bar not modular?</summary>

It is a daily-use personal config, not a framework.
</details>

## Credits

Made by [@tahfizhabib](https://github.com/tahfizhabib).
Built on [Quickshell](https://quickshell.outfoxxed.me) and [Niri](https://github.com/YaLTeR/niri).
