<div align="center">

# ⚙️ ASMLings

### Learn 8086 Assembly Through Interactive Exercises

A `rustlings`-inspired learning environment where you write assembly,
run it instantly, and see if you understand what the CPU does.

[![Crates.io](https://img.shields.io/crates/v/asmlings.svg)](...)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](...)

</div>

<div align="center">

<img src="demo.gif" width="500px" style="border-radius: 4px;">

</div>

ASMLings provides a sandboxed feedback loop powered by a Rust-based 16-bit x86 emulator. You just write code, save the file and instantly check the results.

> Inspired by the `rustlings` project


## Why ASMLings?

Learning assembly is difficult because the feedback loop is slow:

1. Write assembly
2. Assemble it
3. Run it
4. Debug what happened

ASMLings makes it interactive: `write code → save → instant feedback`

Each exercise teaches one concept through small, testable programs.


## Installation

### Using cargo-binstall (fast, no compilation)

```bash
cargo install cargo-binstall
cargo binstall asmlings
```

### Using Cargo (with compilation step)

```bash
cargo install asmlings
```

### Manual Download

Download binaries from the [GitHub Releases page](https://github.com/giacomo-folli/asmlings/releases)

### System Dependency

You must also have the **NASM** assembler installed, as Asmlings uses it under the hood to compile your code before emulation.

* **macOS:** `brew install nasm`
* **Ubuntu/Debian:** `sudo apt install nasm`
* **Arch Linux:** `sudo pacman -S nasm`
* **Windows:** `winget install NASM`

### Troubleshooting Installation (Linux)

If `cargo install asmlings` fails with a linker error mentioning `__atomic_compare_exchange_16` or `undefined symbol`, your system needs the `libatomic` library to compile the underlying CPU emulator.

To fix this, run the installation with the atomic linker flag:

```bash
RUSTFLAGS="-Clink-arg=-latomic" cargo install asmlings

```

*If the compiler says `-latomic` cannot be found, install it via your package manager:*

* **Ubuntu/Debian:** `sudo apt install libatomic1`
* **Arch Linux:** `sudo pacman -S gcc-libs`
* **Fedora/RHEL:** `sudo dnf install libatomic`

---

## Quick Start

Getting started is as simple as running two commands. Navigate to a folder where you want to store your coursework, and run:

### 1. Initialize the Workspace

Extracts the exercise files and sets up your progress tracker.

```bash
asmlings init
```

* **Updating Exercises:** If you already have an `exercises/` directory and want to pull in new exercises from a new release without losing your progress or overwriting your changes, running `asmlings init` will automatically copy only the missing exercises.
* **Resetting Progress:** If you want to overwrite all exercises with fresh templates and reset your progress back to the beginning, run:
  ```bash
  asmlings init --force
  ```

### 2. Start Watch Mode

This launches a persistent watch loop. Leave this running in your terminal!

```bash
asmlings start

```

### 3. Solve the Exercises

Open the newly created `exercises/` folder in your favorite text editor. Asmlings will tell you which file to look at. Follow the instructions in the comments, fix the assembly code, and hit save.

Every time you save, Asmlings will automatically re-assemble and verify your code, providing instant terminal feedback.

*(Note: If you just want to run the current exercise once without watching for file changes, you can use `asmlings run`).*

## How to use
Each exercise in the `exercises/` directory is a self-contained `.asm` file demonstrating standard 8086 instructions (e.g., `mov`, `add`, `push`, `pop`, `lodsb`).

To complete an exercise, you must do two things:

1. **Satisfy the Assertions / Test Cases:** Exercises are verified against dynamic, programmatic test suites with multiple input/setup variations defined under the hood. The CLI will output the results for each assertion in the test cases.
2. **Remove the Sentinel:** Every file contains an `; I AM NOT DONE` comment. Even if your code compiles and passes all assertions and test cases, Asmlings will not advance to the next exercise until you manually delete this line. This ensures you deliberately complete the exercise and understand the solution.

## Who is this for?
ASMLings is for:

- Rust developers wanting to understand what happens below the compiler
- Students learning computer architecture
- Programmers curious about assembly
- Anyone who enjoyed rustlings and wants a low-level challenge

## Contributing
Contributions are welcome! If you'd like to help build or improve Asmlings, check out our [Contributing Guide](CONTRIBUTING.md) for details on setting up your local development environment and troubleshooting common compilation issues.

