# ctsi-rust-sd

![Rust](https://img.shields.io/badge/Rust-000000?style=flat&logo=rust&logoColor=white)
![Cartesi](https://img.shields.io/badge/Cartesi-000000?style=flat&logo=cartesi&logoColor=white)

Experimental Rust-based Cartesi Rollups DApp for Stable Diffusion inference. The project cross-compiles Rust to RISC-V 64-bit (`riscv64gc-unknown-linux-gnu`) and runs inside the Cartesi Machine.

> **Status:** This is a work-in-progress template. The `handle_advance` and `handle_inspect` functions contain TODO placeholders -- the `diffusers-rs` integration was attempted but reverted. The rollup event loop scaffolding is functional.

## Tech Stack

- **Rust 1.72** with Tokio async runtime
- **Hyper** for HTTP client (rollup server communication)
- **Cartesi Rollups SDK 0.6.0**
- **RISC-V cross-compilation** via `riscv64-linux-gnu-g++` linker
- **Docker** multi-stage build (`ubuntu:22.04` builder + `riscv64/ubuntu:22.04` runtime)

## Project Structure

```
testes/
  Cargo.toml          # Dependencies: hyper, tokio, json
  Cargo.lock
  src/main.rs          # Cartesi rollup event loop with advance/inspect handlers
  Dockerfile           # Multi-stage cross-compilation build
  .cargo/config.toml   # RISC-V target and linker configuration
```

## Setup

### Build the Cartesi DApp

```bash
cartesi build
```

### Run

```bash
cartesi run
```

## Related Projects

This is part of the Stable Diffusion on RISC-V project family:
- [cartesi-stable-diffusion](https://github.com/ryanviana/cartesi-stable-diffusion) -- C++ implementation
- [ctsi-sd-cpp](https://github.com/ryanviana/ctsi-sd-cpp) -- C++ from-source build variant
- [sd-with-wheels](https://github.com/ryanviana/sd-with-wheels) -- Python implementation
