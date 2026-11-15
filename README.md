# disk-map

[![Crates.io](https://img.shields.io/crates/v/disk-map.svg)](https://crates.io/crates/disk-map)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/github/actions/workflow/status/disk-map-org/disk-map/ci.yml?branch=main)](https://github.com/disk-map-org/disk-map/actions)

A high-performance Rust CLI for visualizing directory structures and analyzing disk usage with `.gitignore` awareness.

`disk-map` is a modern, cross-platform, and multi-threaded filesystem utility designed to help developers and system administrators understand disk consumption quickly. It combines the functionality of `tree`, `du`, and `find` into a single, efficient tool that respects your project's ignore rules by default.

## Features

*   **Multi-threaded Performance:** Leverages all available CPU cores to traverse large directory trees rapidly.
*   **Smart Filtering:** Automatically respects `.gitignore`, `.git/info/exclude`, and hidden file rules out of the box.
*   **Flexible Layouts:** Choose between a visual tree structure, a compact `du`-style summary, or a detailed table view.
*   **Accurate Metrics:** Reports disk usage in bytes, blocks, or human-readable formats (KB, MB, GB), supporting both logical and physical disk usage.
*   **Advanced Search:** Filter files and directories using glob patterns or regular expressions.
*   **Cross-Platform:** Runs natively on Linux, macOS, and Windows.
*   **Colorized Output:** Supports `LS_COLORS` environment variables for syntax highlighting and file type differentiation.
*   **Granular Control:** Sort results by size, name, or modification time with configurable depth limits.

## Installation

The easiest way to install `disk-map` is via `cargo`, the Rust package manager.

```bash
cargo install disk-map
```

If you prefer a pre-built binary, check the [Releases](https://github.com/disk-map-org/disk-map/releases) page for your operating system.

## Usage

### Basic Tree View
Visualize the current directory structure while ignoring files tracked by `.gitignore`.

```bash
disk-map .
```

### Disk Usage Analysis
Show a summary of disk usage per directory, sorted by size in descending order, limited to a depth of 3 levels.

```bash
disk-map . --sort size --depth 3
```

### Filter Specific Files
Find all Rust source files and display their structure.

```bash
disk-map . --glob "*.rs"
```

## Configuration

`disk-map` supports a configuration file for persistent settings. By default, it looks for a TOML file at `~/.config/disk-map/config.toml`.

Example configuration:

```toml
[defaults]
depth = 3
sort_by = "size"
sort_order = "desc"
show_hidden = false
respect_gitignore = true

[output]
use_colors = true
show_icons = true
```

## License

This project is licensed under the [MIT License](LICENSE).