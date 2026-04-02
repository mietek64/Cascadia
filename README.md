# Cascadia

A terminal rain animation for Windows, Linux, and macOS. Pick a preset, tweak colors and effects through a built-in editor, and run it with one command.

> This is an independent personal project by [mietek64](https://github.com/mietek64). It has no affiliation with Microsoft's Cascadia Code font, The Matrix film franchise, or any other product sharing the name. "Cascadia" here refers to the cascading digital rain aesthetic.

---

## Preview

![Cascadia demo](preview.gif)

---

## Install

### Windows

Download [cascadia.exe](https://github.com/mietek64/Cascadia/releases/latest/download/cascadia.exe) from the latest release, then run the built-in installer:

```powershell
.\cascadia.exe --install
```

This copies `cascadia.exe` to `C:\tools\` and adds it to your PATH. Open a new terminal and type `cascadia`.

If you prefer to do it manually, move `cascadia.exe` to any permanent folder and add that folder to your PATH via `sysdm.cpl`.

### Linux and macOS

No pre-built binary yet. Run from source:

```bash
pip install rich pyfiglet
python main.py -s
```

---

## Usage

```
cascadia              show help and a live preview
cascadia -s           start the rain animation
cascadia -c           open the config editor
cascadia -p           browse and run presets
cascadia -s -f x.json start with a custom config file
cascadia --install    copy to C:\tools\ and set up PATH (Windows)
```

Press `Q` or `Ctrl-C` to quit.

---

## Presets

Run `cascadia -p` to open the preset browser. Pick a number, press `r` to run it or `s` to save it as your default.

| Preset | Description |
|--------|-------------|
| Classic Matrix | Green katakana falling through darkness |
| Cyber Blue | Cyan hex rain with sparkle |
| Blood Rain | Slow crimson latin script |
| Binary Storm | Dense white binary at full speed |
| Ghost Wave | Dim katakana with vignette and a rolling wave |
| Neon Glitch | Magenta hue cycling through chaos |
| Tilt Cascade | Diagonal rain tilting right |
| Deep Space | Sparse dark-green meditative rain |
| Golden Code | Warm amber hex with slow hue drift |

Press `n` in the browser to save your current config as a named preset.

---

## Configuration

Cascadia creates its config automatically the first time you save from the editor. You can find it at:

- Windows: `%APPDATA%\cascadia\config.json`
- Linux/macOS: `~/.config/cascadia/config.json`

Run `cascadia -c` to edit it interactively, or open the JSON file in any text editor.

### All options

| Key | Default | Description |
|-----|---------|-------------|
| `chars` | `katakana` | Character set: `katakana` `latin` `numbers` `binary` `symbols` `hex` `mixed` `custom` |
| `custom_chars` | `""` | Your own character string, used when `chars` is set to `custom` |
| `color` | `#00cc44` | Stream color. Accepts Rich color names, `#rrggbb`, or `rgb(r,g,b)` |
| `head_color` | `bright_white` | Color of the leading character on each stream |
| `speed` | `0.05` | Seconds per frame. Lower is faster (range: 0.01 to 0.50) |
| `density` | `0.04` | Stream spawn probability per column per tick (0 to 0.30) |
| `trail_length` | `20` | Characters per falling stream (3 to 80) |
| `glitch` | `true` | Adds random stray characters across the screen |
| `glitch_chance` | `0.02` | Glitch intensity (0.001 = subtle, 0.20 = heavy) |
| `sparkle` | `false` | Randomly flashes stream cells bright |
| `sparkle_chance` | `0.04` | Fraction of stream cells that sparkle per frame |
| `fade_edges` | `false` | Dims streams near the screen edges |
| `wave` | `false` | Sinusoidal density ripple across columns |
| `wave_speed` | `1.0` | Wave travel speed (0.1 = slow, 10.0 = fast) |
| `rain_tilt` | `0` | Diagonal slant (-5 = left, 0 = straight, 5 = right) |
| `color_cycle` | `false` | Slowly rotates the stream hue over time |
| `color_cycle_speed` | `0.5` | Hue rotation speed (0.05 = slow, 5.0 = fast) |
| `title` | `""` | Text displayed on screen. Leave empty to hide |
| `title_position` | `top-center` | `top-left`, `top-center`, `top-right`, or `center-center` |
| `title_style` | `text` | `text` for a plain label, `ascii` for figlet art (requires pyfiglet) |
| `ascii_font` | `standard` | Figlet font name, for example `doom`, `big`, or `slant` |
| `ascii_size` | `medium` | Font group fallback: `small`, `medium`, or `large` |
| `title_color` | `""` | Title text color. Leave empty to use the stream color |
| `exit_hint` | `true` | Shows a `Q quit` hint in the bottom-right corner |

---

## Build from Source

You need Python 3.13.

**Windows:**

```powershell
py -3.13 -m pip install pyinstaller pyfiglet rich

py -3.13 -m PyInstaller --onefile --console --name cascadia --collect-all rich --collect-all pyfiglet --hidden-import pyfiglet --hidden-import pyfiglet.fonts --exclude-module tkinter --exclude-module unittest --exclude-module email --exclude-module http main.py
```

**Linux / macOS:**

```bash
python3.13 -m pip install pyinstaller pyfiglet rich

python3.13 -m PyInstaller --onefile --console --name cascadia --collect-all rich --collect-all pyfiglet --hidden-import pyfiglet --hidden-import pyfiglet.fonts --exclude-module tkinter --exclude-module unittest --exclude-module email --exclude-module http main.py
```

The output lands at `dist/cascadia.exe` on Windows or `dist/cascadia` on Linux and macOS.

---

## Project Structure

```
Cascadia/
├── main.py            the whole program, one file
├── config.json        default config template
├── pyproject.toml     package metadata
├── README.md
├── LICENSE
├── SECURITY.md
├── CONTRIBUTING.md
├── CHANGELOG.md
└── .gitignore
```

---

## License

MIT. See [LICENSE](LICENSE).

*Cascadia is not affiliated with Microsoft, The Matrix franchise, or any other product using the Cascadia name.*
