

---

##  Vim Normal Mode – Command Cheat Sheet (Zsh with `bindkey -v`)

`ESC` or `jk` နှိပ်ပြီး **cursor နေရာမှာ** ဒီ command တွေ သုံးလို့ရတယ်။

###  Basic Movement

| Key(s) | Action |
|--------|--------|
| `h` | left one char |
| `l` | right one char |
| `j` | down one line (command history) |
| `k` | up one line (command history) |
| `0` (zero) | jump to **beginning** of line |
| `^` | jump to **first non‑blank** character |
| `$` | jump to **end** of line |

###  Word Movement

| Key | Action |
|-----|--------|
| `w` | forward to **start** of next word |
| `b` | backward to **start** of previous word |
| `e` | forward to **end** of word |
| `ge` | backward to **end** of word |

###  Delete / Change / Yank (Copy)

| Key | Action |
|-----|--------|
| `x` | delete character under cursor |
| `dw` | delete from cursor → end of **current word** (space included) |
| `daw` | delete **a word** (including space) |
| `diw` | delete **inner word** (no space) – leaves space |
| `dd` | delete **whole line** |
| `D` | delete from cursor → end of line |
| `cw` | change word (delete + enter insert mode) |
| `cc` | change whole line |
| `yw` | yank (copy) word |

###  Repeat / Undo / Paste / Visual

| Key | Action |
|-----|--------|
| `.` | repeat last change |
| `u` | undo |
| `p` | paste after cursor |
| `P` | paste before cursor |
| `v` | start visual mode (select characters) |
| `V` | start visual line mode |

###  Insert Mode Shortcuts (Bonus)

| Key(s) | Action |
|--------|--------|
| `i` | insert **before** cursor |
| `a` | insert **after** cursor |
| `I` | insert at **beginning** of line |
| `A` | insert at **end** of line |
| `o` | new line below |
| `O` | new line above |
| `jk` or `esc` | return to normal mode |

---


- **ပြင်စရာမလိုဘူး** – Zsh Vi mode မှာ **ဒါတွေ အားလုံးပါပြီးသား**
- **`dw`** က word နဲ့ space ကိုပါ ဖျက်တယ် (whole line မဟုတ်ဘူး)
- **`diw`** က space မပါဘဲ word သက်သက်ကို ဖျက်တယ်
- **`0`**, **`$`**, **`^`** တို့နဲ့ line အစ/အဆုံး သွားလို့ရတယ်

