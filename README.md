<div align="center">

<h1>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="logo_light.svg">
  <img alt="Helix" height="128" src="logo_light.svg">
</picture>
</h1>

[![Build status](https://github.com/helix-editor/helix/actions/workflows/build.yml/badge.svg)](https://github.com/helix-editor/helix/actions)
[![GitHub Release](https://img.shields.io/github/v/release/helix-editor/helix)](https://github.com/helix-editor/helix/releases/latest)
[![Documentation](https://shields.io/badge/-documentation-452859)](https://docs.helix-editor.com/)
[![GitHub contributors](https://img.shields.io/github/contributors/helix-editor/helix)](https://github.com/helix-editor/helix/graphs/contributors)
[![Matrix Space](https://img.shields.io/matrix/helix-community:matrix.org)](https://matrix.to/#/#helix-community:matrix.org)

</div>

![Screenshot](./screenshot.png)

A [Kakoune](https://github.com/mawww/kakoune) / [Neovim](https://github.com/neovim/neovim) inspired editor, written in Rust.

The editing model is very heavily based on Kakoune; during development I found
myself agreeing with most of Kakoune's design decisions.

For more information, see the [website](https://helix-editor.com) or
[documentation](https://docs.helix-editor.com/).

All shortcuts/keymaps can be found [in the documentation on the website](https://docs.helix-editor.com/keymap.html).

[Troubleshooting](https://github.com/helix-editor/helix/wiki/Troubleshooting)

# Features

- Vim-like modal editing
- Multiple selections
- Built-in language server support
- Smart, incremental syntax highlighting and code editing via tree-sitter

Although it's primarily a terminal-based editor, I am interested in exploring
a custom renderer (similar to Emacs) using wgpu.

Note: Only certain languages have indentation definitions at the moment. Check
`runtime/queries/<lang>/` for `indents.scm`.

# Installation

[Installation documentation](https://docs.helix-editor.com/install.html).

[![Packaging status](https://repology.org/badge/vertical-allrepos/helix-editor.svg?exclude_unsupported=1)](https://repology.org/project/helix-editor/versions)

# Contributing

Contributing guidelines can be found [here](./docs/CONTRIBUTING.md).

# Getting help

Your question might already be answered on the [FAQ](https://github.com/helix-editor/helix/wiki/FAQ).

Discuss the project on the community [Matrix Space](https://matrix.to/#/#helix-community:matrix.org) (make sure to join `#helix-editor:matrix.org` if you're on a client that doesn't support Matrix Spaces yet).

# Credits

```toml
[editor.lsp]
# Enable/disable color swatches display (default: true)
display-color-swatches = true

# Customize the color swatch symbol (default: "■")
color-swatches-string = "●"
```

**Configuration Examples:**

```toml
# Circle symbols
[editor.lsp]
color-swatches-string = "●"

# Diamond symbols
[editor.lsp]
color-swatches-string = "◆"

# Hexagon symbols
[editor.lsp]
color-swatches-string = "⬢"

# Alternative hexagon
[editor.lsp]
color-swatches-string = "⬣"

# Default square (explicit)
[editor.lsp]
color-swatches-string = "■"
```

Color swatches appear next to color values in your code (CSS, configuration files, etc.) when LSP support is available, making it easier to visualize colors at a glance.

## Line Movement Commands

**Move Lines Up/Down:**
- `Ctrl+k` - Move current line or selected lines up
- `Ctrl+j` - Move current line or selected lines down

The line movement feature allows you to easily move the current line or multiple selected lines up and down in your document. This works with:
- Single line: When cursor is on a line, moves that entire line
- Multiple selections: Moves all selected lines while preserving their relative positions
- Discontinuous selections: Handles multiple separate line selections correctly
- Unicode content: Properly handles files with Unicode characters

## Noice.nvim-like Command Line (Cmdline)

**Command Line Popup Configuration:**

This fork includes a modern, noice.nvim-inspired command line with customizable icons and popup-style interface.

```toml
[editor.cmdline]
# Command line style: "bottom" (default) or "popup" (noice.nvim style)
style = "popup"

# Show command type icons (default: true)
show-icons = true

# Popup dimensions
min-popup-width = 40    # Minimum width for popup cmdline
max-popup-width = 80    # Maximum width for popup cmdline

# Customize command icons
[editor.cmdline.icons]
search = "🔍"    # For search commands (/,?)
command = "⚙"    # For command mode (:)
shell = "⚡"      # For shell commands (!)
general = "💬"   # For other prompts
```

**Icon Theme Examples:**

```toml
# Minimalist ASCII Style
[editor.cmdline.icons]
search = "/"
command = ":"
shell = "$"
general = ">"

# Nerd Font Icons
[editor.cmdline.icons]
search = ""    # nf-fa-search
command = ""    # nf-fa-cog
shell = ""     # nf-fa-terminal
general = ""   # nf-fa-comment

# Fun Emoji Theme
[editor.cmdline.icons]
search = "🔎"
command = "🛠️"
shell = "🖥️"
general = "📝"

# Disable all icons
[editor.cmdline]
show-icons = false
```

**Features:**
- **Popup-style command line** - Centered floating window instead of bottom line
- **Command type icons** - Visual indicators for different command types
- **Enhanced completion** - Better visual feedback and layout
- **Customizable appearance** - Full control over icons and dimensions
- **Backward compatibility** - Traditional bottom style still available

## Aesthetic Gradient Borders

**Gradient Borders Configuration:**

Transform your Helix interface with beautiful, configurable gradient borders for all pickers and UI components.

```toml
[editor.gradient-borders]
enable = true                    # Enable/disable gradient borders
thickness = 2                   # Border thickness (1-5)
direction = "horizontal"        # "horizontal", "vertical", "diagonal", "radial"
start-color = "#8A2BE2"        # Start color (hex format)
end-color = "#00BFFF"          # End color (hex format)
middle-color = "#FF69B4"       # Optional middle color for 3-color gradients
animation-speed = 3            # Animation speed (0-10, 0 = disabled)
```

**Aesthetic Theme Examples:**

```toml
# Cyberpunk Theme
[editor.gradient-borders]
enable = true
thickness = 2
direction = "horizontal"
start-color = "#FF0080"        # Hot Pink
end-color = "#00FFFF"          # Cyan
animation-speed = 2

# Sunset Theme
[editor.gradient-borders]
enable = true
thickness = 3
direction = "diagonal"
start-color = "#FF4500"        # Orange Red
middle-color = "#FFD700"       # Gold
end-color = "#FF69B4"          # Hot Pink
animation-speed = 1

# Ocean Wave
[editor.gradient-borders]
enable = true
thickness = 2
direction = "vertical"
start-color = "#00CED1"        # Dark Turquoise
end-color = "#4169E1"          # Royal Blue
animation-speed = 4

# Matrix Style
[editor.gradient-borders]
enable = true
thickness = 1
direction = "radial"
start-color = "#00FF00"        # Lime Green
end-color = "#008000"          # Dark Green
animation-speed = 5

# Minimalist (No Animation)
[editor.gradient-borders]
enable = true
thickness = 1
direction = "horizontal"
start-color = "#6A5ACD"        # Slate Blue
end-color = "#9370DB"          # Medium Purple
animation-speed = 0
```

**Border Thickness Styles:**
- **1**: Thin Unicode lines (─│┌┐└┘ square, ─│╭╮╰╯ rounded)
- **2**: Thick Unicode lines (━┃┏┓┗┛)
- **3**: Double Unicode lines (═║╔╗╚╝)
- **4**: Block characters (█ style)
- **5**: Full block characters

**Rounded Corners Support:**
Gradient borders automatically respect your existing `rounded_corners` setting:

```toml
[editor]
# Enable rounded corners for all borders (traditional and gradient)
rounded-corners = true

[editor.gradient-borders]
enable = true
thickness = 1    # Thin borders work best with rounded corners
direction = "horizontal"
start-color = "#6A5ACD"
end-color = "#9370DB"
```

- **Thickness 1**: Full rounded corner support (╭╮╰╯)
- **Thickness 2+**: Uses square corners (no Unicode rounded equivalents)
- **Block styles**: Rounded corners don't apply to block characters

**Features:**
- **Applied to all components**: Pickers, command line popups, completion menus, preview panels
- **Dynamic gradients**: Smooth color transitions across any direction
- **Animation support**: Animated gradients with configurable speed
- **Configurable thickness**: From thin lines to chunky block borders
- **Multiple directions**: Horizontal, vertical, diagonal, and radial patterns
- **3-color gradients**: Optional middle color for more complex gradients
- **Performance optimized**: Efficient rendering with minimal overhead

**Note**: Gradient borders are applied to file pickers, command palettes, completion menus, preview panels, and the noice.nvim-style command line popup. Traditional borders are used when gradient borders are disabled.

## Running app locally on MacOS systems
run the following command on the terminal
`xattr -d com.apple.quarantine /path/to/your/app`
(this removes the quarantine attribute)
