# config-dir-lite

A minimal, dependency-free crate for getting the user's config directory.

## Usage

```rust
use config_dir_lite::config_dir;

fn main() {
    let path = config_dir().expect("config dir");
    println!("{}", path.display());
    // Linux:   /home/alice/.config
    // macOS:   /Users/Alice/Library/Application Support
    //          /Users/Alice/.config (with `favor-xdg-style` feature)
    // Windows: C:\Users\Alice\AppData\Roaming
}
```

## Platform Behavior

| Platform | Path |
|----------|------|
| Linux | `$XDG_CONFIG_HOME` or `$HOME/.config` |
| macOS | `$HOME/Library/Application Support` |
| Windows | `%APPDATA%` |

## Features

- **`favor-xdg-style`** - On macOS, returns `$HOME/.config` instead of `$HOME/Library/Application Support`.

## Platform Conventions

- [XDG Base Directory Specification](https://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html) (Linux)
- [Apple File System Programming Guide](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html) (macOS)
- [Known Folder IDs](https://docs.microsoft.com/en-us/windows/win32/shell/knownfolderid) (Windows)

## Alternatives

Need more? Consider these crates:

- [`dirs`](https://crates.io/crates/dirs) - More directory types (cache, data, etc.)
- [`directories`](https://crates.io/crates/directories) - Project-specific paths with organization support
- [`etcetera`](https://crates.io/crates/etcetera) - Strategy-based (XDG, Apple, Windows)
