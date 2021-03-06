# WRY (Webview Rendering librarY)

Cross-platfrom WebView rendering library in Rust that supports all major desktop platforms like Windows 10, macOS, and Linux.

```toml
[dependencies]
wry = "0.4.0"
```

## Overview

Wry connects the web engine on each platform and provides easy to use and unified interface to render WebView. It uses
[winit] on most platforms and [gtk-rs] on Linux for windows creation.

[winit]: https://crates.io/crates/winit
[gtk-rs]: https://crates.io/crates/gtk

## Usage

The minimum example looks like following:

```rust
use wry::{Application, Result};

fn main() -> Result<()> {
    let mut app = Application::new()?;
    app.create_window(Default::default(), None)?;
    app.run();
    Ok(())
}
```

For more information, please read the documentation below.

## [Documentation](https://docs.rs/wry)

## Platform-specific notes

All platforms uses [winit](https://github.com/rust-windowing/winit) to build the window except Linux. Here are the underlying web engine each platfrom uses and some dependencies you might need to install.

### Linux

Unlike other platforms, [gtk-rs](https://gtk-rs.org/) is used to build the window instead of winit. Because wry needs [WebKitGTK](https://webkitgtk.org/) and winit provides lower level of interface like x11 or wayland. Please make sure WebKitGTK is installed. If not, run the following command:

#### Arch Linux / Manjaro:

```bash
sudo pacman -S webkit2gtk
```

#### Debian / Ubuntu:

```bash
sudo apt install libwebkit2gtk-4.0-dev
```

### macOS

WebKit is native on macOS so everything should be fine.

### Windows

We use EdgeHTML provided by Windows Runtime. So only Windows 10 is supported.

## License
Apache-2.0/MIT
