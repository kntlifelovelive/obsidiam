ဒီ **`color_text()`** ဆိုတာ **Bash function** တစ်ခုပါ။ ၎င်းဟာ **text ကို အရောင်သတ်မှတ်ပြီး print** လုပ်ဖို့အတွက် အသုံးပြုနိုင်ပါတယ်။

---

### **1. Function Definition (တည်ဆောက်ပုံ)**  
```bash
color_text() {
    local color="$1"
    local text="$2"
```
- **`color_text()`** => Function name  
- **`local color="$1"`** => Function ကို call မယ့်အခါ ပထမ **argument** (parameter) ကို `$color` ဟု သိမ်းထားမယ်။  
- **`local text="$2"`** => ဒုတိယ argument ကို `$text` ဟု သိမ်းထားမယ်။  

 **local** ဆိုတာ function ထဲမှာပဲ သက်ဝင်မယ့် variable တွေဆိုလိုတာဖြစ်ပြီး၊ အပြင်မှာတော့ သက်ဝင်မယ့် scope မဟုတ်ပါဘူး။

---

### **2. Case Statement (Color တိုက်စစ်ခြင်း)**
```bash
    case "$color" in
        red)    echo -e "\033[0;31m${text}\033[0m" ;;
        green)  echo -e "\033[0;32m${text}\033[0m" ;;
        blue)   echo -e "\033[0;34m${text}\033[0m" ;;
        *)      echo "$text" ;;  # Default (No color)
    esac
```
- `case "$color" in ... esac`  
  ➜ `case` statement က `$color` variable ရဲ့ **value** ကို check လုပ်ဖို့အသုံးပြုထားတာ။  
- `red)` ➜ `$color` အနေနဲ့ **"red"** ဆိုရင် **`echo -e "\033[0;31m${text}\033[0m"`** ပြုလုပ်မယ်။  
- `green)` ➜ **"green"** ဆိုရင် **`echo -e "\033[0;32m${text}\033[0m"`**  
- `blue)` ➜ **"blue"** ဆိုရင် **`echo -e "\033[0;34m${text}\033[0m"`**  
- `*)` ➜ အခြားကာလာမသတ်မှတ်ရင် default အနေနဲ့ **no color text** ကို print လုပ်မယ်။  

---

### **3. Color Codes (ANSI Escape Codes)**  
🔹 **`\033[0;31m`** ➜ Red  
🔹 **`\033[0;32m`** ➜ Green  
🔹 **`\033[0;34m`** ➜ Blue  
🔹 **`\033[0m`** ➜ Reset (နောက်ထပ် text တွေ အရောင်မထိခိုက်အောင် default ပြန်ထား)  

 **`\033`** ➜ Escape sequence (ANSI color ကို enable လုပ်တာ)  
 **`[0;31m`** ➜ Format code (`31` = Red, `32` = Green, `34` = Blue)  
 **`\033[0m`** ➜ Color ကို **reset** (default text color ပြန်သွားမယ်)  

---

### **4. Function Call (အသုံးပြုခြင်း)**
```bash
color_text red "Error: Something went wrong!"
color_text green "Success: Everything is fine!"
color_text blue "Info: Please wait..."
```
🔹 **`color_text red "Error: Something went wrong!"`**  
    ➜ **Red color** နဲ့ `Error: Something went wrong!` ကို print ပြမယ်။  
🔹 **`color_text green "Success: Everything is fine!"`**  
    ➜ **Green color** နဲ့ success message print မယ်။  
🔹 **`color_text blue "Info: Please wait..."`**  
    ➜ **Blue color** နဲ့ info message print မယ်။  

---

### **Final Output (Terminal မှာ ပြပေးမယ့်အတိုင်း)**  
```bash
Error: Something went wrong!  (in Red)
Success: Everything is fine!   (in Green)
Info: Please wait...           (in Blue)
```
 (အနီ / အစိမ်း / အပြာ) color တွေနဲ့ terminal မှာ output ထွက်မှာပါ။  

 **Note** ➜ Terminal မှာ ANSI color support မရှိရင် အရောင် မပြနိုင်ပါဘူး။ (`echo -e` ကို အသုံးပြုတာက color support လုပ်ဖို့ပါ)  

---

### **Bonus: Extra Colors ထပ်ထည့်ချင်ရင်**
```bash
        yellow) echo -e "\033[0;33m${text}\033[0m" ;; # 🟡 Yellow
        cyan)   echo -e "\033[0;36m${text}\033[0m" ;; # 🟦 Cyan
        purple) echo -e "\033[0;35m${text}\033[0m" ;; # 🟣 Purple
```
Example ➜ `color_text yellow "Warning: Proceed with caution!"`  
(Yellow နဲ့ warning message ထွက်မယ်)  

---

 **Summary**
- Bash function **`color_text()`** ဟာ **text ကို color** ထည့်ပြီး print လုပ်ဖို့အသုံးပြုနိုင်ပါတယ်။
- ANSI **escape codes** (`\033[0;XXm`) ကို သုံးပြီး **terminal text color** ပြောင်းနိုင်ပါတယ်။
- **Case statement** ဖြင့် color ကို switch လုပ်ပြီး handle လုပ်ပါတယ်။
- Extra colors တွေထပ်ထည့်လို့ရပါတယ်။  

---

###  **Bash Terminal မှာ သုံးလို့ရတဲ့ Color Code တွေ**  

Terminal မှာ **Foreground (Text) Colors** နဲ့ **Background Colors** သုံးလို့ရပါတယ်။  
 **Foreground (Text) Color** ➜ `\033[0;Xm`  
**Background Color** ➜ `\033[0;X;Ym`  



##  **1. ANSI Color Code Table**
| Color Name | Foreground (Text) | Background |
|------------|------------------|------------|
| **Black** | `\033[0;30m` | `\033[40m` |
| **Red** | `\033[0;31m` | `\033[41m` |
| **Green** | `\033[0;32m` | `\033[42m` |
| **Yellow** | `\033[0;33m` | `\033[43m` |
| **Blue** | `\033[0;34m` | `\033[44m` |
| **Magenta (Purple)** | `\033[0;35m` | `\033[45m` |
| **Cyan (Light Blue)** | `\033[0;36m` | `\033[46m` |
| **White (Gray)** | `\033[0;37m` | `\033[47m` |

**Example Usage:**  
```bash
echo -e "\033[0;31mRed Text\033[0m"
echo -e "\033[0;32mGreen Text\033[0m"
echo -e "\033[0;33mYellow Text\033[0m"
```

---

##  **2. Background Color ထည့်ပုံ**
Text color နဲ့ Background color **combine** လုပ်လို့ရပါတယ်။  
Format ➜ `\033[TextColor;BackgroundColorm`

🔹 **Example:**  
```bash
echo -e "\033[1;37;41m White Text on Red Background \033[0m"
echo -e "\033[1;30;47m Black Text on White Background \033[0m"
echo -e "\033[1;33;44m Yellow Text on Blue Background \033[0m"
```
🔸 **Explanation:**  
- `\033[1;37;41m` ➜ **White Text (37) on Red Background (41)**  
- `\033[1;30;47m` ➜ **Black Text (30) on White Background (47)**  
- `\033[1;33;44m` ➜ **Yellow Text (33) on Blue Background (44)**  

 **`\033[0m`** ကို နောက်ဆုံးမှာ ထည့်ရတဲ့ အကြောင်းပြချက်က **reset** (default color ပြန်ထားဖို့) ပါ။  

---

##  **3. Bold, Underline, Blinking Effects**
| Effect | Code | Example |
|--------|------|---------|
| **Bold** | `\033[1m` | `echo -e "\033[1mBold Text\033[0m"` |
| **Dim (Faint)** | `\033[2m` | `echo -e "\033[2mDim Text\033[0m"` |
| **Italic** (some terminals) | `\033[3m` | `echo -e "\033[3mItalic Text\033[0m"` |
| **Underline** | `\033[4m` | `echo -e "\033[4mUnderlined Text\033[0m"` |
| **Blinking** | `\033[5m` | `echo -e "\033[5mBlinking Text\033[0m"` |
| **Reversed (Swap FG & BG)** | `\033[7m` | `echo -e "\033[7mReversed Colors\033[0m"` |
| **Hidden (Invisible)** | `\033[8m` | `echo -e "\033[8mHidden Text\033[0m"` |

 **Bold + Color Example**  
```bash
echo -e "\033[1;32mBold Green Text\033[0m"
```

 **Underline + Red Text Example**  
```bash
echo -e "\033[4;31mUnderlined Red Text\033[0m"
```

---

## **4. 256 Color Mode (Advanced)**
**Format:** `\033[38;5;Xm` (Foreground) | `\033[48;5;Xm` (Background)  
🔹 **Example:**  
```bash
echo -e "\033[38;5;82mGreen Text (82)\033[0m"
echo -e "\033[48;5;226mYellow Background (226)\033[0m"
echo -e "\033[38;5;196m\033[48;5;15mRed on White\033[0m"
```

 **256 Color Table** ကို ကြည့်ဖို့  
```bash
for i in {0..255}; do 
    echo -en "\033[48;5;${i}m ${i} \033[0m";
    if (( $i % 16 == 15 )); then echo; fi
done
```
👉 Terminal မှာ Run လိုက်ရင် **256 color preview** ထွက်လာပါမယ်။  

---

##  **5. True Color (24-bit)**
```bash
echo -e "\033[38;2;255;0;0mRed Text\033[0m"
echo -e "\033[48;2;0;255;0mGreen Background\033[0m"
echo -e "\033[38;2;0;255;255m\033[48;2;128;0;128m Cyan on Purple \033[0m"
```
 **`38;2;R;G;B`** ➜ **Foreground (Text)**  
 **`48;2;R;G;B`** ➜ **Background**  

---

## **Summary**
| Type | Example Code | Description |
|------|-------------|-------------|
| **Basic Colors** | `\033[0;31mRed Text\033[0m` | Simple Red Text |
| **Background Colors** | `\033[1;37;41mWhite on Red\033[0m` | White text on Red BG |
| **Bold** | `\033[1mBold Text\033[0m` | Bold text |
| **Underline** | `\033[4mUnderlined\033[0m` | Underlined text |
| **Blinking** | `\033[5mBlinking\033[0m` | Blinking text |
| **256 Colors** | `\033[38;5;82mGreen\033[0m` | 256 Color mode |
| **True Color (RGB)** | `\033[38;2;255;0;0mRed\033[0m` | 24-bit True Color |

---

 **Final Thought**  
- Terminal မှာ **ANSI Escape Codes** သုံးပြီး Color + Effects ထည့်လို့ရတယ်။  
- Background, Foreground တွေ Mix လုပ်နိုင်တယ်။  
- **256 Color Mode** နဲ့ **True Color (RGB)** ကို Support လုပ်တဲ့ Terminal မှာ ပိုပြီး အသုံးဝင်တယ်။  
- Shell Script မှာ သုံးရင် **echo -e** ကို သုံးဖို့လိုမယ်။  

---

##  **256 Color Mode (Advanced)**
**256 Color Mode** ကို သုံးလိုရတဲ့ **Foreground (Text)** နဲ့ **Background Color** တွေကို **ANSI Escape Codes** နဲ့ သုံးနိုင်ပါတယ်။  

###  **1. Basic Syntax**
```bash
\033[38;5;<COLOR_CODE>m  # Foreground (Text)
\033[48;5;<COLOR_CODE>m  # Background
```
**Example:**  
```bash
echo -e "\033[38;5;82mGreen Text (82)\033[0m"
echo -e "\033[48;5;226mYellow Background (226)\033[0m"
echo -e "\033[38;5;196m\033[48;5;15mRed on White\033[0m"
```

---

### ✅ **2. 256 Color Table (Preview in Terminal)**
Terminal မှာ **256 Color Table** ကိုကြည့်ဖို့ အောက်ပါ command ကို run လိုက်ပါ။  
```bash
for i in {0..255}; do 
    echo -en "\033[48;5;${i}m ${i} \033[0m ";
    if (( $i % 16 == 15 )); then echo; fi
done
```
👉 **Run ပြီးရင် Terminal မှာ 256 Color Mode ကို မြင်ရပါလိမ့်မယ်။**  

---

### ✅ **3. Foreground (Text) Color Examples**
```bash
echo -e "\033[38;5;1m Red \033[0m"
echo -e "\033[38;5;2m Green \033[0m"
echo -e "\033[38;5;3m Yellow \033[0m"
echo -e "\033[38;5;4m Blue \033[0m"
echo -e "\033[38;5;5m Purple \033[0m"
echo -e "\033[38;5;6m Cyan \033[0m"
echo -e "\033[38;5;7m White \033[0m"
```

---

### ✅ **4. Background Color Examples**
```bash
echo -e "\033[48;5;1m Red BG \033[0m"
echo -e "\033[48;5;2m Green BG \033[0m"
echo -e "\033[48;5;3m Yellow BG \033[0m"
echo -e "\033[48;5;4m Blue BG \033[0m"
echo -e "\033[48;5;5m Purple BG \033[0m"
echo -e "\033[48;5;6m Cyan BG \033[0m"
echo -e "\033[48;5;7m White BG \033[0m"
```

---

### ✅ **5. Combined Foreground + Background Example**
```bash
echo -e "\033[38;5;226;48;5;88m Yellow Text on Dark Red BG \033[0m"
echo -e "\033[38;5;82;48;5;21m Green Text on Blue BG \033[0m"
echo -e "\033[38;5;196;48;5;15m Red Text on White BG \033[0m"
```

---

💡 **Final Thought**  
- `38;5;<COLOR_CODE>m` ➜ Foreground (Text)  
- `48;5;<COLOR_CODE>m` ➜ Background  
- **Run color table script** ➜ 256 color preview  
- Terminal မှာ သုံးနိုင်တဲ့ Bash script **Gradient Effect** သုံးဖို့လည်း ရပါတယ်။  

---
**256 Color Mode** ရဲ့ **Color Code Table** ကို ပြထားပါတယ်။  
 **Foreground (Text) => `\033[38;5;<COLOR_CODE>m`**  
 **Background => `\033[48;5;<COLOR_CODE>m`**  

---

##  **256 Color Code Table**

<table>
<tr>
<th>Code</th><th>Color</th><th>Code</th><th>Color</th><th>Code</th><th>Color</th><th>Code</th><th>Color</th>
</tr>

<tr><td>0</td><td style="background:#000000;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>1</td><td style="background:#800000;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>2</td><td style="background:#008000;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>3</td><td style="background:#808000;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>4</td><td style="background:#000080;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>5</td><td style="background:#800080;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>6</td><td style="background:#008080;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>7</td><td style="background:#c0c0c0;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>8</td><td style="background:#808080;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>9</td><td style="background:#ff0000;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>10</td><td style="background:#00ff00;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>11</td><td style="background:#ffff00;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>12</td><td style="background:#0000ff;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>13</td><td style="background:#ff00ff;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>14</td><td style="background:#00ffff;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>15</td><td style="background:#ffffff;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>16</td><td style="background:#000000;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>17</td><td style="background:#00005f;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>18</td><td style="background:#000087;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>19</td><td style="background:#0000af;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>20</td><td style="background:#0000d7;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>21</td><td style="background:#0000ff;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>22</td><td style="background:#005f00;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>23</td><td style="background:#005f5f;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>24</td><td style="background:#005f87;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>25</td><td style="background:#005faf;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>26</td><td style="background:#005fd7;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>27</td><td style="background:#005fff;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>28</td><td style="background:#008700;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>29</td><td style="background:#00875f;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>30</td><td style="background:#008787;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>31</td><td style="background:#0087af;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>32</td><td style="background:#0087d7;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>33</td><td style="background:#0087ff;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>34</td><td style="background:#00af00;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>35</td><td style="background:#00af5f;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>36</td><td style="background:#00af87;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>37</td><td style="background:#00afaf;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>38</td><td style="background:#00afd7;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>39</td><td style="background:#00afff;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>40</td><td style="background:#00d700;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>41</td><td style="background:#00d75f;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>42</td><td style="background:#00d787;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>43</td><td style="background:#00d7af;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>44</td><td style="background:#00d7d7;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>45</td><td style="background:#00d7ff;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>46</td><td style="background:#00ff00;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>47</td><td style="background:#00ff5f;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>

<tr><td>48</td><td style="background:#00ff87;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>49</td><td style="background:#00ffaf;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>50</td><td style="background:#00ffd7;">&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>51</td><td style="background:#00ffff;">&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>
</table>


**More colors from 52 - 255 follow the same pattern**  
**Use `for` loop to print the full table in Terminal**

---

##  **Example Usage**
```bash
echo -e "\033[38;5;82mGreen Text (82)\033[0m"
echo -e "\033[48;5;226mYellow Background (226)\033[0m"
echo -e "\033[38;5;196m\033[48;5;15mRed on White\033[0m"
```

✅ **Want Full 256 Colors?** Run This:  
```bash
for i in {0..255}; do 
    echo -en "\033[48;5;${i}m ${i} \033[0m ";
    if (( $i % 16 == 15 )); then echo; fi
done
```

---

## **256 Color Code Table**
### **Usage Format**
- **Foreground (Text Color)** → `\033[38;5;<COLOR_CODE>m`
- **Background (BG Color)** → `\033[48;5;<COLOR_CODE>m`
- **Reset Color** → `\033[0m`

---

### **Example Usage**
```bash
echo -e "\033[38;5;196mRed Text (196)\033[0m"
echo -e "\033[48;5;226mYellow Background (226)\033[0m"
echo -e "\033[38;5;82m\033[48;5;15m Green Text on White BG \033[0m"
```

---

### **Full 256 Color Table**
 Terminal မှာ 256 Color Table အပြည့် တစ်ချက်တည်း ထုတ်ကြည့်ဖို့ Command  
 
```bash
for i in {0..255}; do
    printf "\033[38;5;%sm %3s \033[0m" "$i" "$i"
    if (( (i + 1) % 10 == 0 )); then echo; fi
done
```
 **Color Codes 0 - 255** အတွက် **Foreground Text Color** တွေကို ထုတ်ပြပေးမယ်။

---

### **Full Background Color Table**
 Background Color တွေကို ပြန်ကြည့်ချင်ရင်  
 
```bash
for i in {0..255}; do
    printf "\033[48;5;%sm %3s \033[0m" "$i" "$i"
    if (( (i + 1) % 10 == 0 )); then echo; fi
done
```

**Background Colors 0 - 255** ကို ပြန်ကြည့်လို့ရမယ်။  

---

### **Custom Foreground & Background Together**
**Text Color & Background Color** ကို **Mix** လုပ်ချင်ရင်  

```bash
for i in {0..255}; do
    for j in {0..255}; do
        printf "\033[38;5;%sm\033[48;5;%sm %3s-%3s \033[0m" "$i" "$j" "$i" "$j"
    done
    echo
done
```
**256×256 Color Combination** တွေကို ကြည့်လို့ရမယ်။

---

#### **Color Code အနေနဲ့ 256 Colors မှာ သုံးလို့ရတဲ့ Range**
- **0 - 15** → Standard Colors (Basic ANSI Colors)
- **16 - 231** → 6×6×6 RGB Cube Colors
- **232 - 255** → Grayscale Shades

---


`tput setaf` နဲ့ဆိုင်တဲ့ color codes တွေ၊ function အလုပ်လုပ်ပုံကို Step-by-Step ရှင်းပြပါမယ်။

---

## **1. `tput setaf` Color Codes (Foreground Colors)**
`tput setaf` က **Text Color (Foreground)** ကိုပြောင်းတဲ့ command ဖြစ်ပြီး 0-15 အထိ color codes တွေရှိပါတယ်။ အောက်ပါဇယားကို ကြည့်ပါ။

| Code | Color          | Example (အရောင်) |
| ---- | -------------- | ---------------- |
| 0    | Black          | ██████████████   |
| 1    | Red            | ██████████████   |
| 2    | Green          | ██████████████   |
| 3    | Yellow         | ██████████████   |
| 4    | Blue           | ██████████████   |
| 5    | Magenta        | ██████████████   |
| 6    | Cyan           | ██████████████   |
| 7    | White          | ██████████████   |
| 8    | Bright Black   | ██████████████   |
| 9    | Bright Red     | ██████████████   |
| 10   | Bright Green   | ██████████████   |
| 11   | Bright Yellow  | ██████████████   |
| 12   | Bright Blue    | ██████████████   |
| 13   | Bright Magenta | ██████████████   |
| 14   | Bright Cyan    | ██████████████   |
| 15   | Bright White   | ██████████████   |
|      |                |                  |
|      |                |                  |

**သိထားရမှာ:**  
- `setaf` = **Set A**ctive **F**oreground (လက်ရှိ text color ပြောင်းခြင်း)
- `setab` = **Set A**ctive **B**ackground (နောက်ခံ color ပြောင်းခြင်း)  
  (ဥပမာ - `$(tput setab 1)` = နောက်ခံအနီရောင်)

---

## **2. `color_text()` Function အလုပ်လုပ်ပုံ**
သင့်ရဲ့ function ကို အဆင့်လိုက်ရှင်းပြပါမယ်။

### **Function Code:**
```bash
color_text() {
    local color="$1"   # ပထမဆုံး argument (color name)
    local text="$2"    # ဒုတိယ argument (ပုံသွင်းမယ့် text)
    
    case "$color" in
        redwhite)    # "redwhite" ဆိုရင်
            # Red Text (1) + White Background (7) + Bold
            echo -e "\n$(tput bold)$(tput setaf 1)$(tput setab 7)${text}$(tput sgr0)\n"
            ;;
        yellowwhite)  # "yellowwhite" ဆိုရင် (မှတ်ရန်: yellowhite မဟုတ်)
            # Yellow Text (3) + White Background (7) + Bold
            echo -e "\n$(tput bold)$(tput setaf 3)$(tput setab 7)${text}$(tput sgr0)\n"
            ;;
        *)           # ဘာ color မှမဟုတ်ရင်
            echo "$text"  # Default (အရောင်မပါ)
            ;;
    esac
}
```

---

### **အဆင့်ဆင့်ရှင်းလင်းချက်:**
1. **`tput bold`**  
   → Text ကို Bold လုပ်ပေးတယ်

2. **`tput setaf 1`**  
   → Text Color ကို **အနီရောင်** လုပ်ပေးတယ် (code 1)

3. **`tput setab 7`**  
   → Background Color ကို **အဖြူရောင်** လုပ်ပေးတယ် (code 7)

4. **`$(tput sgr0)`**  
   → ပြင်ထားတဲ့ style တွေအားလုံးကို **Reset** လုပ်တယ် (ပုံမှန်အခြေအနေပြန်ဖြစ်အောင်)

5. **`echo -e "\n...\n"`**  
   → Text ရဲ့ အထက်အောက်မှာ **new lines** ထပ်ဖြည့်ပေးတယ် (`-e` က escape characters တွေကို enable လုပ်ပေးတယ်)

---

## **3. ဥပမာတွေနဲ့ စမ်းသပ်ကြည့်ခြင်း**
### **Example (1): Red Text + White Background**
```bash
color_text redwhite "Hello World"
```
**Output:**  
![Red on White Text](https://i.imgur.com/3XmFQ9l.png)

---

### **Example (2): Yellow Text + White Background**
```bash
color_text yellowwhite "Testing Colors"
```
**Output:**  
![Yellow on White Text](https://i.imgur.com/9GjKv2W.png)

---

### **Example (3): Uppercase လုပ်ချင်ရင်**
မူရင်း code မှာ `sed` command က color codes တွေကို ဖျက်ပစ်လို့ uppercase လုပ်တဲ့အခါ **အရောင်မပါ** တော့ပါဘူး။  
**အဆင်ပြေအောင် ပြင်ဆင်နည်း ၂ မျိုး:**

#### **နည်း ၁: `sed` ကိုဖြုတ်ပြီး `awk` နဲ့ပဲသုံးမယ်**
```bash
color_text yellowwhite "$namevariable" | awk '{print toupper($0)}'
```

#### **နည်း ၂: အရင် Uppercase လုပ်ပြီးမှ Color ထည့်မယ်**
```bash
uppercased_text=$(echo "hello world" | awk '{print toupper($0)}')
color_text yellowwhite "$uppercased_text"
```

---

## **4. Terminal မှာ Color Support ရှိမရှိစစ်ဆေးခြင်း**
- Terminal က color တွေကို support လုပ်မလုပ်သိချင်ရင် အောက်ပါ command ရိုက်ပါ။  

  ```bash
  tput colors
  ```
- **Output:** `8` (or more) ဆိုရင် color တွေအလုပ်လုပ်ပါတယ်။

---

## **5. အခြား Color Combinations တွေကိုစမ်းချင်ရင်**
ဥပမာ - **Blue Text (4) + Cyan Background (6)** လုပ်ချင်ရင်:

```bash
echo "$(tput setaf 4)$(tput setab 6)This is Blue on Cyan$(tput sgr0)"
```

---

**အရေးကြီးတဲ့အချက်:**  
- `setaf` နဲ့ `setab` codes တွေကို လိုသလို ပြောင်းသုံးလို့ရပါတယ်။
- Color name တွေကို case-sensitive ဖြစ်တာမို့ (ဥပမာ - `yellowwhite` ≠ `yellowWhite`) သတိထားပါ။
---

