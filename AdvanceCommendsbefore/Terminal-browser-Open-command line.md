
*Terminal ကနေ browser ကိုဖွင့်ဖို့အတွက် command line tools တွေသုံးလို့ရပါတယ်။ **Linux** တွင်အောက်ပါနည်းလမ်းများဖြင့် browser ကိုဖွင့်နိုင်ပါတယ်။*

### 1. **Default Browser ကိုဖွင့်ရန်**
```bash
xdg-open https://www.example.com
```
- `xdg-open` က default application (browser, file manager, etc.) ကိုသုံးပြီး URL ကိုဖွင့်ပေးပါတယ်။  
- Example:  
```bash
xdg-open https://google.com
```

### 2. **Specific Browser အသုံးပြုရန်**
- **Firefox**  
```bash
firefox https://www.example.com
```
- **Google Chrome**  
```bash
google-chrome https://www.example.com
```
- **Brave Browser**  
```bash
brave-browser https://www.example.com
```

### 3. **Terminal Browser အသုံးပြုရန်**  
GUI browser မလိုဘဲ terminal မှာသာ browsing လုပ်ချင်ရင် **lynx**၊ **w3m** လိုမျိုး tools တွေသုံးနိုင်ပါတယ်။  

**lynx ကို install ပြုလုပ်ရန်**  
```bash
sudo apt update
sudo apt install lynx
```
**lynx မှာ website browsing**  
```bash
lynx https://www.example.com
```

**w3m ကို install ပြုလုပ်ရန်**  
```bash
sudo apt install w3m
```
**w3m မှာ website browsing**  
```bash
w3m https://www.example.com
```

### 4. **အသုံးပြုမှုများ**  
- GUI Browser ကို background မှာဖွင့်ရန်  
```bash
firefox https://google.com &
```
- Tab အသစ်ဖြင့်ဖွင့်ရန်  
```bash
firefox --new-tab https://google.com
```
- Window အသစ်ဖြင့်ဖွင့်ရန်  
```bash
firefox --new-window https://google.com
```

---
