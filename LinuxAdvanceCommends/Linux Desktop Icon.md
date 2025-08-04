

**Linux Desktop Icon** ဆိုတာက Desktop ပေါ်မှာ တစ်ခုတစ်ခုကို တိုက်ရိုက် ဖွင့်နိုင်ဖို့ အသုံးပြုတဲ့ လင့်ခ်ပဲ ဖြစ်ပါတယ်။ ဒီအိုင်ကွန်တွေက `.desktop` ဖိုင်များအဖြစ်ရှိပြီး အဓိကအားဖြင့် GNOME၊ KDE၊ XFCE တို့မှာ အသုံးပြုပါတယ်။

**Desktop Entry (.desktop file)** မှာ ပါဝင်တဲ့ အဓိကဖိုင်ဖွဲ့စည်းပုံကို ရှင်းပြပါမယ်။

---

###  **Desktop Entry Format**

`example.desktop` 

```ini
[Desktop Entry]
Name=My Application
Comment=This is a sample application
Exec=/usr/bin/myapp --no-sandbox
Icon=/usr/share/icons/myapp.png
Terminal=false
Type=Application
Categories=Utility;Application;
```



####  **Field Breakdown**

1. **[Desktop Entry]**
    
    - ဒီ Line က Desktop Entry ဖိုင်တစ်ခုဖြစ်ကြောင်း ကြေညာတာပါ။
2. **Name**
    
    - Desktop ပေါ်မှာ ပြထားမယ့် အိုင်ကွန်နာမည်ပါ။
    - ဥပမာ - `Name=My Application`
3. **Comment**
    
    - Mouse ကို Icon ပေါ်မှာ တင်ထားရင် Popup အနေနဲ့ ပြမယ့် အကြောင်းအရာပါ။
    - ဥပမာ - `Comment=This is a sample application`
4. **Exec**
    
    - Command သို့မဟုတ် Program path ပါ။
    - ဥပမာ - `Exec=/usr/bin/myapp`
5. **Icon**
    
    - အိုင်ကွန်ရဲ့ ပုံလမ်းကြောင်းကို သတ်မှတ်ပါတယ်။
    - ဥပမာ - `Icon=/usr/share/icons/myapp.png`
6. **Terminal**
    
    - Command ကို Terminal မှာ ဖွင့်ဖို့လိုမလိုသတ်မှတ်တာပါ။
    - `true` သို့မဟုတ် `false`
    - ဥပမာ - `Terminal=false`
7. **Type**
    
    - Entry ရဲ့ အမျိုးအစားဖြစ်ပြီး `Application`, `Link`, `Directory` စတာတွေ ရှိပါတယ်။
    - ဥပမာ - `Type=Application`
8. **Categories**
    
    - Application Menu တွေမှာ ပြသဖို့ Category သတ်မှတ်တာပါ။
    - ဥပမာ - `Categories=Utility;Application;`

---

###  **Desktop Entry ဖိုင် ပြုလုပ်နည်း**

**Step 1:** Desktop Folder မှာ `.desktop` ဖိုင် ဖန်တီးပါ။

```bash
sudo subl /usr/share/applications/example.desktop 
```

**Step 2:** အထဲမှာ အောက်ပါအတိုင်း ရေးထည့်ပါ။

```ini
[Desktop Entry]
Name=My App
Comment=Run My Custom Application --no-sandbox
Exec=/home/user/myapp.sh
Icon=/home/user/myicon.png
Terminal=true
Type=Application
Categories=Utility;
```

**Step 3:** ဖိုင်ကို စနစ်အသိအမှတ်ပြုအောင် လုပ်ပါ။

```bash
chmod +x ~/usr/share/applications/example.desktop
```

---

###  **Icon မပေါ်ရင် ပြဿနာအဖြေ**

1. **Permission** ကို အရင်စစ်ပါ။

```bash
ls -l ~/usr/share/applications/example.desktop
```

2. **Exec Path** မှားယွင်းမှုရှိလား စစ်ပါ။
    
3. **Icon Path** မှန်လား စစ်ပါ။
    

---

