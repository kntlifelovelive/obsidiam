## **Awk String Functions Table**  

| **Function**       | **Description (ရှင်းလင်းချက်)** | **Example** | **Output** |
|-------------------|------------------------------|------------|---------|
| `length(s)`      | String `s` ရဲ့ အရှည်ကိုတွက်သည် | `length("Hello")` | `5` |
| `toupper(s)`     | String `s` ကို uppercase ပြောင်းသည် | `toupper("hello")` | `HELLO` |
| `tolower(s)`     | String `s` ကို lowercase ပြောင်းသည် | `tolower("HELLO")` | `hello` |
| `substr(s, p, n)` | String `s` ထဲမှ `p` နေရာကနေ `n` characters ကိုထုတ်သည် | `substr("Hello",2,3)` | `ell` |
| `index(s, t)`    | String `s` ထဲမှာ `t` ကိုရှာပြီး index တန်ဖိုးပြန်သည် (မတွေ့ရင် `0`) | `index("hello world", "world")` | `7` |
| `match(s, r)`    | String `s` ထဲမှာ regex `r` ကိုရှာပြီး position တန်ဖိုးပြန်သည် | `match("hello", /l+/)` | `3` |
| `sub(r, t, s)`   | `s` ထဲက `r` ကို `t` ဖြင့် တစ်ခုပဲ ပြောင်းသည် | `sub(/l/, "L", "hello")` | `heLlo` |
| `gsub(r, t, s)`  | `s` ထဲက `r` ကို `t` ဖြင့် **အားလုံး** ပြောင်းသည် | `gsub(/l/, "L", "hello")` | `heLLo` |
| `split(s, a, d)` | String `s` ကို delimiter `d` ဖြင့် array `a` ထဲ ခွဲသည် | `split("a,b,c", arr, ",")` | `arr[1]="a", arr[2]="b"` |
| `sprintf(fmt, args...)` | C-style formatting ပြုလုပ်သည် | `sprintf("%.2f", 3.14159)` | `3.14` |

---

### **Examples**
```bash
echo 'hello world' | awk '{print toupper($0)}'
# Output: HELLO WORLD

echo 'hello world' | awk '{print substr($0, 1, 5)}'
# Output: hello

echo 'hello world' | awk '{sub(/world/, "awk"); print}'
# Output: hello awk
```


## **length(s) - String Length**
String **အရှည်** (character count) ကိုတွက်နိုင်တယ်။  
```bash
echo "Hello World" | awk '{print length($0)}'
# Output: 11
```
✔ `$0` သည် line တစ်ကြောင်းလုံးကို ကိုယ်စားပြုသည်။  
✔ `"Hello World"` မှာ **11 characters** ရှိတယ်။  

## **toupper(s) - Uppercase**
String တစ်ခုကို **uppercase** ပြောင်းနိုင်တယ်။  
```bash
echo "hello world" | awk '{print toupper($0)}'
# Output: HELLO WORLD
```
✔ `hello` → `HELLO`, `world` → `WORLD`  

## **tolower(s) - Lowercase ပြောင်း**
String တစ်ခုကို **lowercase** ပြောင်းနိုင်တယ်။  
```bash
echo "HELLO WORLD" | awk '{print tolower($0)}'
# Output: hello world
```
✔ `HELLO` → `hello`, `WORLD` → `world`  


## **substr(s, p, n) - Substring**
String **တစ်ခုထဲက အချို့အပိုင်း** ကိုထုတ်နိုင်တယ်။  
```bash
echo "Hello World" | awk '{print substr($0, 7, 5)}'
# Output: World
```
✔ `substr($0, 7, 5)` မှာ `7` ဆိုတာ start position  
✔ `5` ဆိုတာ character count  
✔ `"Hello World"` မှာ 7th position ကနေ **5 characters** (`World`) ထုတ်ထားတယ်။  


## **index(s, t) - String Position**
String **တစ်ခုထဲမှာ keyword တစ်ခု ဘယ်နေရာမှာ ရှိလဲ** တွက်နိုင်တယ်။  
```bash
echo "hello world" | awk '{print index($0, "world")}'
# Output: 7
```
✔ `"world"` ဟာ `"hello world"` ထဲမှာ **7th character** မှစတင်တယ်။  


## **match(s, r) - Regular Expression Match**
String ထဲမှာ **regex pattern** ကိုရှာပြီး **တည်နေရာ** ပြန်ပေးနိုင်တယ်။  
```bash
echo "hello world" | awk '{print match($0, /o+/)}'
# Output: 5
```
✔ `o+` ဆိုတာ `o` တစ်ခု သို့မဟုတ် အများကြီး **ဆက်တိုက်ပါနေတဲ့နေရာ** ကို ရှာမယ်။  
✔ `"hello world"` မှာ `o` တွေထဲက **5th character** မှစတင်ပေါ်လာတယ်။  


## **sub(r, t, s) - Replace First Match**
`r` ဆိုတဲ့ pattern ကို `t` ဖြင့် **တစ်ခုပဲ** ပြောင်းနိုင်တယ်။  
```bash
echo "hello world" | awk '{sub(/l/, "L", $0); print}'
# Output: heLlo world
```
✔ `l` ကို `L` ဖြင့် **ပထမဆုံး တစ်ခုတည်းသာ** ပြောင်းပေးတယ်။  


## **gsub(r, t, s) - Replace All Matches**
Pattern **အားလုံးကို** ပြောင်းနိုင်တယ်။  
```bash
echo "hello world" | awk '{gsub(/l/, "L", $0); print}'
# Output: heLLo worLd
```
✔ `l` တွေအားလုံးကို `L` ပြောင်းလိုက်ပြီ။  



## **split(s, a, d) - String ကို Array ခွဲမယ်**
String ကို delimiter `d` ဖြင့် **array** တစ်ခုထဲသို့ ခွဲနိုင်တယ်။  
```bash
echo "apple,banana,orange" | awk '{split($0, arr, ","); print arr[1], arr[2], arr[3]}'
# Output: apple banana orange
```
✔ `,` (comma) ကို delimiter အနေနဲ့ သုံးပြီး string ကို ခွဲလိုက်တယ်။  
✔ `arr[1] = apple`, `arr[2] = banana`, `arr[3] = orange`  


## **sprintf(fmt, args...) - Formatting**
C-style **string formatting** ပြုလုပ်နိုင်တယ်။  
```bash
echo | awk '{num = 3.14159; print sprintf("%.2f", num)}'
# Output: 3.14
```
✔ `%.2f` ဆိုတာ floating point ကို **decimal 2 နေရာထိ** ပြပါ။  
✔ `3.14159` → `3.14`  



## **Full Example**
```bash
echo "hello world" | awk '
{
    print "Original: " $0
    print "Length: " length($0)
    print "Uppercase: " toupper($0)
    print "Lowercase: " tolower($0)
    print "Substring (7,5): " substr($0, 7, 5)
    print "Index of 'world': " index($0, "world")
    sub(/l/, "L", $0)
    print "After sub(): " $0
    gsub(/l/, "L", $0)
    print "After gsub(): " $0
}'
```
✔ **Output:**  
```bash
Original: hello world
Length: 11
Uppercase: HELLO WORLD
Lowercase: hello world
Substring (7,5): World
Index of 'world': 7
After sub(): heLlo world
After gsub(): heLLo worLd
```

## **Summary**
| **Function** | **အသုံးပြုမှု** |
|-------------|----------------|
| `length(s)` | String ရဲ့ အရှည်တွက်မယ် |
| `toupper(s)` | Uppercase ပြောင်းမယ် |
| `tolower(s)` | Lowercase ပြောင်းမယ် |
| `substr(s, p, n)` | Substring ထုတ်မယ် |
| `index(s, t)` | String ထဲမှာ pattern ရှာမယ် |
| `match(s, r)` | Regular expression match |
| `sub(r, t, s)` | ပထမဆုံး match ကိုပြောင်းမယ် |
| `gsub(r, t, s)` | Matches အားလုံးကို ပြောင်းမယ် |
| `split(s, a, d)` | String ကို array ခွဲမယ် |
| `sprintf(fmt, args...)` | C-style formatting |

---
---

Bash နဲ့ Zsh မှာ **length function** ကို ရေးဖို့ နည်းလမ်း အမျိုးမျိုးရှိပါတယ်။  

### **`awk` သုံးပြီး Function**
```bash
str_length_awk() {
    echo "$1" | awk '{print length($0)}'
}
```
**အသုံးပြုမှု:**  
```bash
var="Hello World"
echo "Length: $(str_length_awk "$var")"
```
✔ **Output:** `Length: 11`


### **`wc -m` သုံးပြီး Function**  
(`wc -m` သည် newline ကိုပါ ထည့်တွက်နိုင်မလို့ `tr -d '\n'` ထည့်ထားသည်)
```bash
str_length_wc() {
    echo -n "$1" | wc -m
}
```
**အသုံးပြုမှု:**  
```bash
var="Hello World"
echo "Length: $(str_length_wc "$var")"
```
✔ **Output:** `Length: 11`


### **`${#var}` (Built-in Bash & Zsh Method)**  
```bash
str_length_builtin() {
    echo "${#1}"
}
```
**အသုံးပြုမှု:**  
```bash
var="Hello World"
echo "Length: $(str_length_builtin "$var")"
```
✔ **Output:** `Length: 11`


### **Bonus: One-liner**
```bash
echo "Length: ${#var}"
```
✔ **အမြန်ဆုံး နည်းလမ်းပါ။**  
✔ **Bash & Zsh နှစ်ခုလုံးအတွက် အလုပ်လုပ်တယ်။** 



#### **AWK အခြေခံ (Basic AWK)**

AWK ဟာ **pattern scanning** နဲ့ **text processing** အတွက် scripting language ဖြစ်ပြီး, Linux/Unix CLI တွင် data parsing နှင့် manipulation လုပ်ဖို့ အထူးသင့်တော်ပါတယ်။


#### **AWK Command Structure**

AWK ရဲ့ syntax အခြေခံရိုးရိုးက 

```bash
awk 'pattern {action}' file
```

1. **Pattern**: အဘယ်သူမျှမပါပါက၊ File ရဲ့ **line** တိုင်းကို process လုပ်မည်။
2. **Action**: `{}` အတွင်းမှာလုပ်ဆောင်မည့် action တွေ (e.g., print, calculation) ကိုရေးရန်။
3. **File**: Process လုပ်မည့် file name။

### **Basic Examples**

#### **1. File Read နဲ့ Print**
```bash
awk '{print $0}' file.txt
```
- **$0**: Line တစ်ခုလုံးကို print လုပ်တယ်။
- `file.txt` ရဲ့ အရာအားလုံးကို output ပြမည်။


#### **2. Specific Field ကို Print**
```bash
awk '{print $1, $3}' file.txt
```
- `$1`: 1st column
- `$3`: 3rd column
- Columns တွေကို space ဖြင့် ခွဲထားသည်။


#### **3. Conditional Statements**
```bash
awk '$3 > 50 {print $1, $3}' file.txt
```
- 3rd column value > 50 ဖြစ်သော lines မှ 1st နဲ့ 3rd columns ကို print လုပ်တယ်။


#### **4. Pattern Matching**
```bash
awk '/error/ {print $0}' log.txt
```
- "error" ပါသော lines ကို output ပြမည်။


#### **5. BEGIN နဲ့ END Blocks**
- **BEGIN**: File ကို process မစခင် တစ်ကြိမ် run တယ်။
- **END**: File process ပြီးမှ run တယ်။
```bash
awk 'BEGIN {print "Start"} {print $0} END {print "End"}' file.txt
```
Output:
```
Start
(Line 1)
(Line 2)
End
```


### **AWK Functions**
1. **Length of a String**:
   ```bash
   awk '{print length($0)}' file.txt
   ```
2. **Substrings**:
   ```bash
   awk '{print substr($2, 1, 3)}' file.txt
   ```
   - 2nd column ကနေ စတာ 3 characters ထိ။
3. **Math Functions**:
   ```bash
   awk '{print sqrt($3), sin($3)}' file.txt
   ```


## **AWK(Advanced AWK)**

AWK ကို ဖြည်းဖြည်းတိုးချဲ့ပြီး complex tasks တွေအတွက် အသုံးပြုနိုင်ပါတယ်။

### **1. Arrays in AWK**
AWK မှာ associative arrays ကို support လုပ်တယ်။
```bash
awk '{count[$1]++} END {for (word in count) print word, count[word]}' file.txt
```
- File ရဲ့ 1st column တွေကို count လုပ်တယ်။


### **2. Custom Delimiters**
Default delimiter က **space** ပါပေမဲ့, OFS (Output Field Separator) နဲ့ FS (Field Separator) ကို ပြောင်းနိုင်တယ်။
```bash
awk -F ',' '{print $1, $2}' file.csv
```
- `-F ','`: Comma-separated file ကို process လုပ်တယ်။


### **3. Writing Complex Scripts**
AWK script ကို `.awk` file အနေနဲ့ ရေးသားနိုင်တယ်။

#### **Example Script (script.awk):**
```awk
BEGIN {
    print "Name\tScore"
    print "------------"
}
{
    if ($2 >= 50)
        print $1 "\t" $2
}
END {
    print "Done Processing"
}
```
Run Command:
```bash
awk -f script.awk file.txt
```


### **4. Working with Multiple Files**
```bash
awk 'FNR==1 {print "Processing " FILENAME} {print $0}' file1.txt file2.txt
```
- `FNR`: Each file's line number.
- `FILENAME`: Current file name.


### **5. Regular Expressions**
AWK နဲ့ powerful pattern matching လုပ်နိုင်ပါတယ်။
```bash
awk '/^Start/ {print $0}' file.txt
```
- Lines starting with "Start" only.


### **6. Dynamic Variables (Assigning from CLI)**
```bash
awk -v threshold=50 '$3 > threshold {print $1, $3}' file.txt
```
- CLI ကနေ `threshold` variable ထည့်သွင်းနိုင်တယ်။


### **7. Gawk Specific Features**
Gawk မှာ advanced functions တွေ ရှိတယ်:
- **Working with JSON**:
   ```bash
   gawk 'BEGIN { print tojson(["name", "age", "location"]) }'
   ```
- **TCP/UDP Sockets**:
   ```bash
   gawk 'BEGIN { print "GET /" |& "/inet/tcp/0/www.example.com/80" }'
   ```


## **AWK Best Practices**
1. **Use BEGIN/END blocks for clarity.**
2. **Keep scripts modular and reusable.**
3. **Test with small data files first.**
4. **Use `gawk` for advanced processing tasks.**
5. **Linux Log Files ကို analyze လုပ်ဖို့ try လုပ်ပါ။**
6. **Online challenges (e.g., Kaggle data analysis) တွေကို အလေ့အကျင့်လုပ်ပါ။**
7. **Official AWK Documentation** (GNU Gawk Manual) ကို ဖတ်ပါ။

AWK နဲ့ Gawk ကို basic မှ advanced tasks အထိ ကျွမ်းကျင်လာမယ်ဆိုရင်, logs analysis, data processing, automation တွေအတွက် အရမ်းအသုံးဝင်ပါတယ်။ 

---
