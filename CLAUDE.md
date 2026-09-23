# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build

The only Rust toolchain in the Ubuntu container is Termux's (target `aarch64-linux-android`). Plain `cargo build` fails at link time (`cannot find -llog` / `-lunwind`) because it picks up Ubuntu's `ld`. Point cargo at Termux's clang:

```bash
CARGO_TARGET_AARCH64_LINUX_ANDROID_LINKER=/data/data/com.termux/files/usr/bin/clang cargo run
```

Running `cargo` from the Termux host shell needs no override.
