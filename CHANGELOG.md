# Changelog

All notable changes are documented here.

---

## [1.1.0] — 2026

### Added
- `--install` flag — copies `matrix.exe` to `C:\tools\` and adds it to the user PATH
  automatically via the Windows registry. No admin rights, no PowerShell scripts, no sysdm.cpl.
- PowerShell one-liner install option documented in README

### Changed
- Version bumped to `1.1.0`
- Updated `rich` dependency to `>=14.3.3`
- Updated `pyfiglet` dependency to `>=1.0.4`
- README install section rewritten with three options (built-in, one-liner, manual)
- Linux/macOS pre-built binary removed from README — not yet available, source instructions provided instead

---

## [1.0.0] — 2026

Initial public release.

### Features
- Matrix rain animation with full RGB color support via the `rich` library
- 9 built-in presets: Classic Matrix, Cyber Blue, Blood Rain, Binary Storm,
  Ghost Wave, Neon Glitch, Tilt Cascade, Deep Space, Golden Code
- Interactive TUI config editor (`matrix -c`) with live color swatches and section grouping
- Preset browser (`matrix -p`) with run, save, and custom preset save/delete
- No-args splash screen with figlet title, command reference, mini rain preview, and tips
- Character sets: katakana (half-width), latin, numbers, binary, symbols, hex, mixed, custom
- Effects: glitch, sparkle, fade edges, wave, rain tilt, color cycle
- Title overlay: text or ASCII art (pyfiglet), with position and color control
- Config auto-created at `%APPDATA%\matrix\config.json` (Windows) or `~/.config/matrix/config.json`
- Custom presets persisted to `presets.json` alongside config
- Stable 2D grid rendering — no position drift, no wrapping artifacts
- Resize-aware: clears and rebuilds streams on terminal resize
- Q / Esc / Ctrl-C to quit
- Standalone `.exe` build via PyInstaller (no Python required to run)

### Technical notes
- Half-width katakana (`0xFF66–0xFF9E`) used to avoid 2-column-wide character drift
- `rich.live` with `vertical_overflow="crop"` and `no_wrap=True` for stable full-screen rendering
- Hue cycling implemented via RGB rotation matrix (no HSL conversion needed)
- Figlet art lines normalized to uniform width before anchor calculation to prevent per-frame drift
- `argparse` group set to non-required — no args shows splash instead of argparse error
