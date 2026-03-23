# sentry-crashpad

[![PyPI version](https://img.shields.io/pypi/v/sentry-crashpad.svg)](https://pypi.org/project/sentry-crashpad/)

Python wheel distribution of [Crashpad](https://chromium.googlesource.com/crashpad/crashpad/)
from [sentry-native](https://github.com/getsentry/sentry-native). Packages the
`crashpad_handler` executable so it can be installed via pip without a C++ toolchain.

Used by [Endstone](https://github.com/EndstoneMC/endstone) for crash reporting.

## Installation

```bash
pip install sentry-crashpad
```

This installs the `crashpad_handler` command:

```bash
crashpad_handler --help
```

## Versioning

The version in `sentry_version.txt` maps to
[sentry-native releases](https://github.com/getsentry/sentry-native/releases). The build
system downloads the matching sentry-native source and compiles `crashpad_handler` from it.

An optional fourth digit (e.g. `0.12.6.1`) is used for packaging-only changes that don't
change the upstream sentry-native version.

## Building from Source

Requires a C++ toolchain (MSVC on Windows, GCC on Linux, Apple Clang on macOS):

```bash
pip install .
```

## Releasing

The release workflow builds wheels for all platforms (Linux x86_64/aarch64/i686, Windows
x86/AMD64, macOS x86_64/arm64) and publishes to PyPI.

**Via tag:** push a tag like `v0.12.6` to trigger automatically.

**Via workflow_dispatch:** go to Actions > Build + Release Wheels > Run workflow. You can
override the sentry version and wheel packaging version, and choose between PyPI and TestPyPI.

## License

[Apache-2.0](LICENSE)