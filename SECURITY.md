# Security Policy

## Supported Versions

Only the latest release receives security fixes.

## Reporting a Vulnerability

Please don't open a public issue for security vulnerabilities.

Report them privately through GitHub's security advisory system:

1. Go to the [Security tab](https://github.com/mietek64/Cascadia/security) of this repo
2. Click "Report a vulnerability"
3. Describe the issue in as much detail as you can

You'll get a response within 72 hours. If the report is confirmed, a fix goes out as soon as possible and you'll be credited in the release notes unless you'd prefer to stay anonymous.

## Scope

Cascadia is a terminal animation tool. At runtime it makes no network connections, has no user accounts, and writes only to a local config file when you explicitly save from the editor. The config parser uses Python's standard `json` module with no `eval` or `exec`, so a malformed config file can't execute code.

The only meaningful attack surface is the supply chain: the runtime dependencies are `rich` and `pyfiglet`, both widely used PyPI packages.

## Pre-built Binary

The `cascadia.exe` in Releases is built with PyInstaller directly from `main.py` in this repo. If you want to verify it, build it yourself following the instructions in the README and compare the output.

Windows Defender may flag the binary as suspicious. This is a known false positive caused by PyInstaller's bootloader, not anything in the code.
