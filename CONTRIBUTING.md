# Contributing

All contributions are welcome, whether that's a bug report, a new preset, a feature idea, or a code change.

This is a personal side project, so response times may vary, but good pull requests will be reviewed and merged.

## Running from Source

You need Python 3.13.

```bash
git clone https://github.com/mietek64/Cascadia
cd Cascadia
pip install rich pyfiglet
python main.py
```

There's no test suite. This is a visual terminal app, so the main way to verify a change is to run it and look at it across a few different terminal sizes and configs.

## Making a Change

Fork the repo, create a branch off `main`, and keep each pull request focused on one thing.

If you're adding a config option, add it to `DEFAULT_CONFIG`, add an entry to `SCHEMA` so it appears in the `-c` editor, and document it in the README options table. If it's interesting enough to be a preset, add it to `BUILTIN_PRESETS` too.

If you're adding a preset, give it a unique `id`, a clear `name`, and a short `desc`. Make sure every config key you use exists in `DEFAULT_CONFIG`.

Once you're done, open a pull request and describe what you changed and why.

## Commit Style

Plain English, present tense, short:

```
add sparkle to Cyber Blue preset
fix tilt spawn gap at screen edges
update README install instructions
```

## Code Style

Python 3.13, no dependencies beyond `rich` and `pyfiglet`. No linting is enforced, just match the existing style. Keep the section separators (`# ═══...`) around major blocks.

## License

By submitting a pull request you agree your contribution is released under the [MIT License](LICENSE).
