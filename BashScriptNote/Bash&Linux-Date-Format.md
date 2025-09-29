
## `date` command အခြေခံအသုံးပြုခြင်း  
Linux terminal မှာ `date` တစ်ခြား options မပါဘဲ ထည့်ရင် system time & date ကို ပြမယ်။  
```bash
date
```
ဥပမာ output:  
```
Sat Feb  8 12:34:56 PM UTC 2025
```

## Format ပြောင်းပြီး ပြသခြင်း  
`date` command ကို `+` နဲ့ တခြား format string တွေထည့်ပြီး ပြင်ဆင်နိုင်ပါတယ်။  

### Common format strings  
| Format | Description | Example Output |
|--------|------------|---------------|
| `%Y` | Year (4 digits) | `2025` |
| `%y` | Year (2 digits) | `25` |
| `%m` | Month (01-12) | `02` |
| `%d` | Day (01-31) | `08` |
| `%H` | Hour (00-23) | `12` |
| `%I` | Hour (01-12) | `12` |
| `%M` | Minute (00-59) | `34` |
| `%S` | Second (00-59) | `56` |
| `%p` | AM or PM | `PM` |
| `%A` | Full weekday name | `Saturday` |
| `%a` | Short weekday name | `Sat` |
| `%B` | Full month name | `February` |
| `%b` | Short month name | `Feb` |
| `%Z` | Timezone | `UTC` |

### Format အသုံးပြုမှု ဥပမာများ  
1. **YYYY-MM-DD format**  
```bash
date "+%Y-%m-%d"
```
**Output:**  
```
2025-02-08
```

2. **DD/MM/YYYY format**  
```bash
date "+%d/%m/%Y"
```
**Output:**  
```
08/02/2025
```

3. **Time only (HH:MM:SS AM/PM)**  
```bash
date "+%I:%M:%S %p"
```
**Output:**  
```
12:34:56 PM
```

4. **Full Date & Time**  
```bash
date "+%A, %B %d, %Y - %I:%M %p"
```
**Output:**  
```
Saturday, February 08, 2025 - 12:34 PM
```

## Future & Past Dates တွေတွက် Calculation  
### ၁ ရက် နောက်ထပ်မြှောက်လိုက်မယ်  
```bash
date -d "+1 day"
```
**Output:**  
```
Sun Feb  9 12:34:56 UTC 2025
```

### ၇ ရက်နောက် (1 week later)  
```bash
date -d "+7 days"
```

### ၁ လ နောက်  
```bash
date -d "+1 month"
```

### ၁ လ မတိုင်ခင် (1 month ago)  
```bash
date -d "-1 month"
```

## Unix Timestamp (Epoch Time)  
Unix timestamp ဆိုတာ 1970-01-01 00:00:00 UTC ကစပြီး ဆက်တိုက် ရက်တွေကို seconds နဲ့တွက်ထားတဲ့ value ဖြစ်ပါတယ်။  

- **Current timestamp ကို ထုတ်ကြည့်ခြင်း**  
```bash
date "+%s"
```
**Output:**  
```
1739049296
```

- **Timestamp ကို Human Readable ပြောင်းခြင်း**  
```bash
date -d @1739049296
```
**Output:**  
```
Sat Feb  8 12:34:56 UTC 2025
```

## System Time ကို Change လုပ်ခြင်း  
Root 权限 (sudo) လိုအပ်တယ်။  
```bash
sudo date -s "2025-02-08 14:00:00"
```

## Conclusion  
- `date` ကို အချိန် & ရက်စွဲ ပြရန်အသုံးပြုနိုင်သည်  
- Format တွေကို `+%Y-%m-%d` နဲ့ ပြောင်းနိုင်သည်  
- Future / Past dates တွေကို `-d "+1 day"` နဲ့ တွက်နိုင်သည်  
- Unix timestamp ကို သိလိုရင် `%s` format ကိုအသုံးပြုနိုင်သည်  
- System time ကို sudo ဖြင့် ပြောင်းနိုင်သည်  
---
---

**ပြုပြင်ပုံ:**  
`I` ကို **escaped** (`\I`) လုပ်ပေးရမယ်။  

```bash
date +"\I cannot believe it's already %A!"
```
ဒါမှမဟုတ် **single quotes** သုံးလို့ရတယ်။  
```bash
date +'I cannot believe it'"'"'s already %A!'
```
ဒါကြောင့် `I` ဟာ `%I` နဲ့ ပျော်လွှာမနေသလို၊ `'` (single quote) က string တွေကို မှားအသုံးပြုတာ မဖြစ်အောင် `"'"` (single-quote escaped) သုံးတာ ဖြစ်ပါတယ်။  

**မှားနေတဲ့အကြောင်းရင်း:**  
`date` မှာ format specifier (`%` နဲ့စတဲ့ format codes) တွေကို သုံးရတာမလွယ်ဘူး။ `%I` ဆိုတာ **Hour in 12-hour format** ဆိုလိုတာပါ။  
```bash
date +"%I"
```
ဆိုရင် `12` (12-hour format) လို့ output ပြမယ်။  
ဒါကြောင့် `I` ကို `\` escape မလုပ်ရင် `%I` လိုက်ရှာပြီး ကြေညာမလို့ error ဖြစ်တယ်။

---