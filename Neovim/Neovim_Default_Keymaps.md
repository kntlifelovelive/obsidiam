# Neovim Default Keymaps

## 🔹 Normal Mode
| Keymap | Description |
|--------|------------|
| `:w` | Save File |
| `:q` | Quit Neovim |
| `:wq` | Save & Quit |
| `:qa!` | Force Quit All |
| `u` | Undo |
| `Ctrl + r` | Redo |
| `yy` | Copy Line |
| `p` | Paste |
| `dd` | Cut Line |
| `x` | Delete Character |
| `D` | Delete until end of line |
| `cc` | Change (Delete & Enter Insert Mode) |
| `J` | Join Lines |
| `>>` | Indent Line |
| `<<` | Unindent Line |
| `~` | Toggle Case |
| `.` | Repeat Last Command |
| `:%s/old/new/g` | Replace All Instances |

## 🔹 Insert Mode
| Keymap | Description |
|--------|------------|
| `jk` | Exit Insert Mode |
| `Ctrl + U` | Delete Line Before Cursor |
| `Ctrl + W` | Delete Word Before Cursor |
| `Ctrl + H` | Delete Character Before Cursor |
| `Ctrl + D` | Decrease Indent |
| `Ctrl + T` | Increase Indent |
| `Ctrl + R` | Paste Register Content |

## 🔹 Visual Mode
| Keymap | Description |
|--------|------------|
| `v` | Enter Character-wise Visual Mode |
| `V` | Enter Line-wise Visual Mode |
| `Ctrl + V` | Enter Block-wise Visual Mode |
| `y` | Copy Selection |
| `d` | Cut Selection |
| `p` | Paste |

## 🔹 Command Mode
| Keymap | Description |
|--------|------------|
| `:noh` | Clear Search Highlights |
| `:e <filename>` | Open a File |
| `:vs <filename>` | Split Window Vertically |
| `:sp <filename>` | Split Window Horizontally |
| `:tabnew` | Open New Tab |
| `:tabn` | Next Tab |
| `:tabp` | Previous Tab |

## 🔹 Window Navigation
| Keymap | Description |
|--------|------------|
| `Ctrl + w h` | Move Left |
| `Ctrl + w l` | Move Right |
| `Ctrl + w j` | Move Down |
| `Ctrl + w k` | Move Up |
| `Ctrl + w v` | Split Vertical |
| `Ctrl + w s` | Split Horizontal |
| `Ctrl + w q` | Close Window |
| `Ctrl + w =` | Balance Windows |

## 🔹 Buffer & Tab Navigation
| Keymap | Description |
|--------|------------|
| `:bn` | Next Buffer |
| `:bp` | Previous Buffer |
| `:bd` | Close Buffer |
| `gt` | Next Tab |
| `gT` | Previous Tab |

## 🔹 Plugins (LazyVim Specific)
| Keymap | Description |
|--------|------------|
| `<leader>ff` | Find File |
| `<leader>fg` | Live Grep |
| `<leader>fb` | Find Buffer |
| `<leader>fh` | Find Help Tags |

---
> **💡 Note:** This file contains default Neovim keymaps including LazyVim shortcuts.
