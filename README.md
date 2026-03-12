# clip-paste.nvim

clip-paste.nvim is a small Neovim plugin that automatically enables
clipboard integration between WSL and Windows.

It checks whether `clip.exe` and `powershell.exe` are available. If they
are, the plugin configures Neovim to use the Windows clipboard. If not,
it does nothing. This allows the same Neovim configuration to work
across different operating systems without manual changes.

## Why

When sharing dotfiles between Windows/WSL, macOS, and Linux, clipboard
configuration often needs to be commented or toggled manually. This
plugin removes that step by enabling the integration only when the
required Windows tools are present.

## Requirements

-   Neovim 0.10+
-   `clip.exe`
-   `powershell.exe`

Typically these are available in WSL with Windows interop enabled, and
on native Windows.

## Installation

Using lazy.nvim:

``` lua
{
  "pugarte7/clip-paste.nvim",
  lazy = false,
}
```

Using packer:

``` lua
use "pugarte7/clip-paste.nvim"
```

## Usage

No setup is required. The plugin runs automatically on startup.

If `clip.exe` and `powershell.exe` are found in PATH, clipboard
integration is enabled. Otherwise, the plugin exits silently.

## What it does

When active, the plugin sets `vim.g.clipboard` so that:

-   copy uses `clip.exe`
-   paste uses `powershell.exe Get-Clipboard`
-   carriage returns are normalized

