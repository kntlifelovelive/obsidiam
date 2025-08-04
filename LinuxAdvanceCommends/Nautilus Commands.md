---

---


## Nautilus CLI options တွေကို အသုံးပြုပြီး File Manager ကို manage လုပ်နိုင်ပါတယ်။

## `nautilus` command နဲ့ options တွေကို **Terminal** မှာ အသုံးပြုနိုင်ပါတယ်။

### Nautilus Command Options

Nautilus CLI မှာ အသုံးများတဲ့ options -

| **Command** | **Function** |
| --- | --- |
| `nautilus` | Default Nautilus window ကိုဖွင့်မယ် |
| `nautilus <path>` | တစ်သီးပုခေါ် ဖိုင်ဒါကိုဖွင့်မယ် |
| `nautilus -w` | **New Window** တစ်ခုဖွင့်မယ် |
| `nautilus -q` | Nautilus ကို **Quit** (Process ပိတ်မယ်) |
| `nautilus --no-desktop` | Desktop Icons ကို မပြဘဲ ဖွင့်မယ် |
| `nautilus --browser` | Browser-style view mode ကိုဖွင့်မယ် |
| `nautilus --check` | Nautilus setup ကို စစ်ဆေးမယ် |
| `nautilus --version` | Nautilus ရဲ့ version ကို ပြမယ် |

* * *

### `-w` `Option` အကြောင်း

**`nautilus -w`** ဆိုတာ **Nautilus New Window** ကိုဖွင့်ဖို့ အသုံးပြုပါတယ်။

**Usage Example**:

```bash
nautilus -w
```

ဒါဆို Nautilus ရဲ့ window တစ်ခုပေါင်းပြီး ဖွင့်လိမ့်မယ်။

* * *

### တခြား နည်းလမ်းတွေနဲ့ Nautilus ဖွင့်ရန်

1.  **Specific Folder ဖွင့်ခြင်း**:
    
    ```bash
    nautilus ~/Documents
    ```
    
    - **`~/Documents`** ဆိုတာ Home Directory ထဲက **Documents** ဖိုင်ဒါကို ဖွင့်တာဖြစ်ပါတယ်။
2.  **Desktop Icons ကို မဖွင့်ချင်ရင်**:
    
    ```bash
    nautilus --no-desktop
    ```
    
3.  **New Window Mode ကို Always Browser Style**:
    
    ```bash
    nautilus --browser
    ```
    
4.  **ပိတ်ပြီးသွားတဲ့ Nautilus Process ကို Restart လုပ်ခြင်း**:
    
    ```bash
    nautilus -q
    ```
    

* * *

### Nautilus Options ကို Help Command နဲ့ ကြည့်ရန်

**Help menu** ကို ကြည့်ချင်ရင်:

```bash
nautilus --help
```

ဒီ command ကို အသုံးပြုလျှင် Nautilus ရဲ့ အားလုံးသော options များကို ပြသပေးပါလိမ့်မယ်။

* * *

### နောက်ထပ် အသုံးဝင်တဲ့ Tips

Nautilus ကို `sudo` နဲ့ Root Permission ဖွင့်ချင်ရင်:

```bash
sudo nautilus
```

ဒါဆို **Root** access နဲ့ Nautilus window ကို open လုပ်နိုင်ပါလိမ့်မယ်။

* * *

**Nautilus** command-line options ရဲ့ အကျဉ်းချုပ်ဖြစ်ပါတယ်။ `-w`, `--no-desktop`, `-q` လို option တွေက အသုံးများပါတယ်။

* * *

# Nautilus GUI

1.  **Applications Menu** ထဲက **Files** (Nautilus) ကို ဖွင့်နိုင်ပါတယ်။
2.  **Shortcut Key**: `Super + E` (Windows key ကို Super key လို့ ခေါ်တယ်) ကို နှိပ်လိုက်ရင် Nautilus ကို တန်းဖွင့်လို့ရပါတယ်။
3.  **Folder Explorer**:
    - File တွေကို Browse, Copy, Move, Delete လုပ်နိုင်ပါတယ်။
    - **Right Click** လုပ်ပြီး **New Folder** တစ်ခုသစ်ဖန်တီးနိုင်ပါတယ်။
4.  **Bookmarks**:
    - သေသပ်တဲ့ folder ကို **Bookmarks** ထဲထည့်ဖို့ `Ctrl + D` ကို သုံးပါ။
5.  **Search**:
    - **`Ctrl + F`** ကို နှိပ်ပြီး လိုချင်တဲ့ ဖိုင်/ဖိုင်ဒါ ကိုရှာနိုင်ပါတယ်။

* * *

### Nautilus Command Line:

Terminal ထဲမှာ Nautilus ကို CLI command နဲ့အသုံးပြုနိုင်ပါတယ်။

1.  **Nautilus ကို ဖွင့်ရန်**:
    
    ```bash
    nautilus
    ```
    

***ဒီ command ကို ရိုက်လိုက်ရင် Desktop မှာ Nautilus window က ဖွင့်လာပါလိမ့်မယ်။***

2.  **Directory Open cli:**:
    
    ```bash
    nautilus /path/to/directory
    ```
    
    **Example**: Home folder ကို ဖွင့်ချင်ရင်
    
    ```bash
    nautilus ~
    ```
    
3.  **Background မှ Nautilus ကို ဖွင့်ရန်**:  
    **Nautilus ကို **Background Mode** မှာဖွင့်ဖို့ `&` နဲ့ တစ်ပြိုင်နက်သုံးနိုင်ပါတယ်။**
    
    ```bash
    nautilus /path/to/directory &
    ```
    
4.  **Nautilus Full-screen Mode:**
    
    ```bash
    nautilus --no-desktop
    ```
    
5.  **Terminal မှ Nautilus Close:**
    
    Nautilus ကို စတင်ဖွင့်ပြီးပြီဆိုရင် Task ထဲမှာ run လုပ်နေစေချင်တဲ့အခါ ပိတ်ချင်ရင်
    
    ```bash
    pkill nautilus
    ```
    

* * *

## Nautilus GUI Shortcuts:

| **Shortcut Key** | **Function** |
| --- | --- |
| `Ctrl + N` | New Nautilus Window |
| `Ctrl + T` | Open a New Tab |
| `Ctrl + W` | Close Current Tab |
| `Ctrl + H` | Show/Hide Hidden Files |
| `Ctrl + L` | Go to Location Bar |
| `Alt + Left` | Go Back |
| `Alt + Right` | Go Forward |
| `F5` | Refresh Current View |
| `Ctrl + Shift + N` | Create a New Folder |

* * *

### Nautilus Extensions

Nautilus ကို ပိုမိုစွယ်စုံစေဖို့ **Extensions** တွေကို တပ်ဆင်နိုင်ပါတယ်။

**Example**:

1.  **Nautilus Terminal**: Nautilus ထဲမှာ Terminal ပေါ်စေတဲ့ Extension.
    
    ```bash
    sudo apt install nautilus-terminal
    ```
    
    ပြီးရင် Nautilus ကို restart လုပ်ဖို့:
    
    ```bash
    nautilus -q
    ```
    
2.  **Nautilus Admin**: Nautilus မှ **Root Permission**
    
    ```bash
    sudo apt install nautilus-admin
    ```
    
    Restart Nautilus:
    
    ```bash
    nautilus -q
    ```
    

* * *

### Nautilus Restart

Nautilus ကို Refresh/Restart လုပ်ချင်ရင်:

```bash
nautilus -q
```

***Nautilus process Refresh/Restart***

* * *

