# Changelog

---

## [1.2.0] — 2026

### Added
- Rain tilt dead-space fix: stream spawn range now extends off-screen by the exact amount tilt can drift, filling edge gaps at any tilt value
- Title rendering now transparent: ASCII art and text titles no longer block rain behind them — only the actual glyphs are drawn, spaces show through

### Changed
- `title_bg` removed from the config editor and default config. The option still works if you set it manually in your JSON file, but it no longer appears in the `-c` editor since background-less titles look better
- `head_bright` removed from the config editor and default config. It was listed as an option but nothing in the code read it
- `tilt_pad` moved out of the per-frame loop and recomputed only on terminal resize
- Project renamed from Matrix to Cascadia

---

## [1.1.0] — 2026

### Added
- `--install` flag: copies `cascadia.exe` to `C:\tools\` and adds it to the user PATH via the Windows registry. No admin rights, no PowerShell scripts, no `sysdm.cpl`

### Changed
- Version bumped to `1.1.0`
- Updated `rich` dependency to `>=14.3.3`
- Updated `pyfiglet` dependency to `>=1.0.4`

---

## [1.0.0] — 2026

Initial public release.

### Features
- Rain animation with full RGB color support via `rich`
- 9 built-in presets: Classic Matrix, Cyber Blue, Blood Rain, Binary Storm, Ghost Wave, Neon Glitch, Tilt Cascade, Deep Space, Golden Code
- Interactive TUI config editor (`cascadia -c`) with live color swatches
- Preset browser (`cascadia -p`) with run, save, and custom preset save/delete
- No-args splash screen with figlet title, command reference, mini rain preview, and tips
- Character sets: half-width katakana, latin, numbers, binary, symbols, hex, mixed, custom
- Effects: glitch, sparkle, fade edges, wave, rain tilt, color cycle
- Title overlay: plain text or ASCII art via pyfiglet, with position and color control
- Config auto-created at first save
- Custom presets saved to `presets.json` alongside config
- Stable 2D grid rendering with no position drift or wrapping artifacts
- Resize-aware: clears and rebuilds streams on terminal resize
- Standalone `.exe` via PyInstaller, no Python required to run
