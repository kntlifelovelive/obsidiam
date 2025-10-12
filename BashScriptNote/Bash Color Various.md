
Bash နဲ့ Zsh ထဲမှာ **Color Variables** ကို သတ်မှတ်ပြီး အသုံးပြုနည်းကို ပြပါမယ်။  

####  **Basic Method (Using ANSI Escape Codes)**  

```bash
# Define color variables
RED='\033[0;31m'
GREEN='\033[0;32m'
BLUE='\033[0;34m'
RESET='\033[0m'  # Reset color to default

# Use colors in echo
echo -e "${RED}This is red text.${RESET}"
echo -e "${GREEN}This is green text.${RESET}"
echo -e "${BLUE}This is blue text.${RESET}"
```

**🔹 Note:** `\033` (or `\e`) ကို **ANSI escape code** လို့ခေါ်ပြီး **color formatting** တွေမှာသုံးတာပဲ။  
**🔹 `${RESET}` ကို မထည့်ရင် color တွေက apply ဖြစ်နေမယ်။**

####  **Advanced Method (Using Associative Arrays in Zsh)**  
Zsh မှာ **Associative Arrays** သုံးလို့ရတယ်။  
```zsh
typeset -A COLORS
COLORS=(
  red    '\033[0;31m'
  green  '\033[0;32m'
  blue   '\033[0;34m'
  reset  '\033[0m'
)

# Example usage
echo -e "${COLORS[red]}This is red.${COLORS[reset]}"
echo -e "${COLORS[green]}This is green.${COLORS[reset]}"
```
**🔹 Note:** `typeset -A` ကို `declare -A` အဖြစ် **Bash 4+** မှာသုံးလို့ရပေမယ့် **Zsh ရဲ့ Associative Array** နဲ့ ပိုကောင်းတယ်။  

#### **Function Method (More Readable & Reusable)** 

```bash

color_text() {
    local color="$1"
    local text="$2"
    case "$color" in
        red)    echo -e "\033[0;31m${text}\033[0m" ;;
        green)  echo -e "\033[0;32m${text}\033[0m" ;;
        blue)   echo -e "\033[0;34m${text}\033[0m" ;;
        *)      echo "$text" ;;  # Default (No color)
    esac
}

color_text red "Error: Something went wrong!"
color_text green "Success: Everything is fine!"
color_text blue "Info: Please wait..."

```

**🔹 Note:** Function သုံးပြီး color **switching** လုပ်တာက **Reusable & Clean** ဖြစ်တယ်။  

###  **Zsh Prompt Customization with Colors**  

```zsh

autoload -U colors && colors  # Enable color support in Zsh

PROMPT="%{$fg[red]%}➜ %{$fg[green]%}%~ %{$reset_color%}"

```

**🔹 Note:** `%{$fg[color]%}` သုံးပြီး Zsh Prompt ကို သတ်မှတ်လို့ရတယ်။  


```bash

color_text() {
    local color="$1"
    local text="$2"
    case "$color" in
        redwhite)    echo  "\n\033[3m\033[1;31;47m${text}\033[0m\n" ;;
        yellowhite)   echo  "\n\033[3;1;34;47m${text}\033[0m\n" ;;
        *)      echo "$text" ;;  # Default (No color)
    esac
}

namevariable="hello world"

color_text yellowhite "$namevariable" | awk '{print toupper($0)}'



```


 `awk '{print toupper($0)}'` က အလုပ်မလုပ်တာက `color_text` function ထဲမှာ escape character `\033` တွေပါနေလို့ပါ။   
- `echo` ဟာ `\033[...]` ANSI escape sequences တွေကို terminal မှာ render လုပ်ပေးတယ်။  
- **Pipe (`| awk '{print toupper($0)}'`) မှာ escape character တွေပါနေလို့, awk က အရင်ကဲ့သို့ output ကို upper case ပြောင်းပေးမနိုင်တဲ့ ပြဿနာ ဖြစ်လာတယ်။**  

### ဖြေရှင်းနည်း  
**1. `echo -e` ကို အသုံးပြုပါ။**  
```bash
color_text() {
    local color="$1"
    local text="$2"
    case "$color" in
        redwhite)    echo -e "\n\033[3m\033[1;31;47m${text}\033[0m\n" ;;
        yellowhite)  echo -e "\n\033[3;1;34;47m${text}\033[0m\n" ;;
        *)           echo "$text" ;;  # Default (No color)
    esac
}

namevariable="hello world"

color_text yellowhite "$namevariable" | awk '{print toupper($0)}'
```
`echo -e` သုံးပြီးရင် escape sequence တွေကို စနစ်တကျ render ပြုလုပ်နိုင်လိမ့်မယ်။  

**2. `awk` မှာ color strip လုပ်ပြီး ပြောင်းမယ်။**  
```bash
color_text yellowhite "$namevariable" | sed 's/\x1B\[[0-9;]*m//g' | awk '{print toupper($0)}'
```
 `sed` ကိုသုံးပြီး **ANSI color codes ကို strip** လုပ်ပြီးမှ `awk` အတွက် uppercase ပြောင်းနိုင်မယ်။  

**3. `tput` ကို သုံးမယ် (ပိုကောင်းတဲ့နည်းလမ်း)**  
```bash
color_text() {
    local color="$1"
    local text="$2"
    case "$color" in
        redwhite)    echo -e "\n$(tput bold)$(tput setaf 1)$(tput setab 7)${text}$(tput sgr0)\n" ;;
        yellowhite)  echo -e "\n$(tput bold)$(tput setaf 3)$(tput setab 7)${text}$(tput sgr0)\n" ;;
        *)           echo "$text" ;;  # Default (No color)
    esac
}

namevariable="hello world"

color_text yellowhite "$namevariable" | awk '{print toupper($0)}'
```
 **`tput` သုံးလို့ escape character problem မဖြစ်တော့ဘူး။**  

### `tput` ဆိုတာဘာလဲ?  

`tput` ဟာ **terminal ထဲမှာ color, text styles, cursor control, screen clearing** စတဲ့ **terminal properties တွေကို handle လုပ်နိုင်တဲ့ command-line utility** တစ်ခုပဲ။  

####  `tput` ကိုဘာလို့သုံးကြတာလဲ?  

 **ANSI escape sequences (`\033[...m`) ကို မသုံးဘဲ**, portable ဖြစ်တဲ့နည်းလမ်းဖြင့် **terminal color & formatting** တွေကို control လုပ်နိုင်လို့။  
**Shell scripting မှာ cross-platform compatibility ကောင်း** တယ်။  
**Different terminal types** (xterm, Linux console, tmux, etc.) မှာလည်း အလုပ်ဖြစ်တယ်။  


###  `tput` နဲ့ Color & Text Formatting  
`tput` ကို အသုံးပြုလိုက်ရင် color, bold, reset, background color တွေကို အလွယ်တကူ handle လုပ်နိုင်တယ်။  

####  Foreground Color (Text Color)  
```bash
tput setaf N
```

🔹 **N** ဟာ **color number** ဖြစ်ပြီး **0-7** ဖြစ်နိုင်တယ်။  

| Color | Code |
|--------|------|
| Black  | `tput setaf 0` |
| Red    | `tput setaf 1` |
| Green  | `tput setaf 2` |
| Yellow | `tput setaf 3` |
| Blue   | `tput setaf 4` |
| Magenta| `tput setaf 5` |
| Cyan   | `tput setaf 6` |
| White  | `tput setaf 7` |


```bash
echo "$(tput setaf 1)Hello in Red$(tput sgr0)"
```

####  Background Color  
```bash
tput setab N
```
🔹 `setab` က background color ကိုပြောင်းဖို့ပါ။  

```bash
echo "$(tput setab 4)$(tput setaf 7)Blue Background with White Text$(tput sgr0)"
```

####  Bold Text  
```bash
tput bold
```
```bash
echo "$(tput bold)This is Bold$(tput sgr0)"
```

####  Reset Formatting (Restore Default)  
```bash
tput sgr0
```
==> `sgr0` ဟာ text formatting (bold, color, etc.) ကို default ပြန်ပြောင်းပေးတယ်။  
```bash
echo "$(tput bold)Bold Text$(tput sgr0) Normal Text"
```

### Example: Colored & Styled Output  
```bash
echo "$(tput bold)$(tput setaf 2)Green Bold Text$(tput sgr0)"
echo "$(tput setaf 1)$(tput setab 7)Red Text on White Background$(tput sgr0)"
```
=> **Bold green text + Red text with white background**  
=> `tput sgr0` သုံးထားလို့ formatting reset ဖြစ်သွားမယ်။  

### `tput` ကို Function ထဲသုံးမယ်  
```bash
color_text() {
    local color="$1"
    local text="$2"
    
    case "$color" in
        redwhite)    echo -e "$(tput bold)$(tput setaf 1)$(tput setab 7)${text}$(tput sgr0)" ;;
        yellowwhite) echo -e "$(tput bold)$(tput setaf 3)$(tput setab 7)${text}$(tput sgr0)" ;;
        *)          echo "$text" ;;
    esac
}

namevariable="hello world"
color_text redwhite "$namevariable"
```
==> **function ကိုသုံးလိုက်ရင်**  
 `color_text redwhite "Hello World"` ဆိုရင် **Red text on White background**  
`color_text yellowwhite "Hello World"` ဆိုရင် **Yellow text on White background**  


###  `tput` ကို သုံးလို့ရတဲ့ အကျိုးကျေးဇူး  
=> **Escape sequences မလိုတော့ဘူး** (`\033[...m` ကို တိုင်းနဲ့ မှတ်စရာမလိုတော့ဘူး)  
=> **Linux, macOS, BSD, tmux, screen, different terminals တွေမှာ compatible ဖြစ်တယ်**  
=> **Script တွေထဲမှာ သုံးရင် ကောင်းလွန်းတယ်**  

####  `tput` ကို အဲ့လိုသုံးကြည့်ပြီး **script တွေမှာ colors & formatting တွေကို professional လို ထည့်သုံးနိုင်ပါပြီ။**

---

