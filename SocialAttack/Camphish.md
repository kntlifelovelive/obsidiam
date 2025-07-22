
---

## 🐟 CamPhish!!!  What the hell ?

CamPhish ကတော့ **phishing tool** တစ်ခုပဲဖြစ်ပြီး၊ ဖုန်းကင်မရာကို request ပေးပြီး photo capture လုပ်နိုင်အောင်လုပ်ထားတာပါ။ Ngrok, Cloudflared တို့နဲ့ tunnel ပြုပြင်ပြီး victim ကို phishing link ပေးပြီး သူတို့ရဲ့ camera access ကို ယူနိုင်ပါတယ်။

🔴 **Ethical Hacking / Educational Lab တွင်သာ အသုံးပြုသင့်ပါတယ်။**

---

## အသုံးပြုပုံ (Usage Instructions)

### 1. Clone CamPhish

```bash
git clone https://github.com/techchipnet/CamPhish
cd CamPhish
chmod +x camphish.sh
```

### 2. Run the Script

```bash
./camphish.sh
```

### 3. Choose Tunnel Option

CamPhish မှာ tunneling tools ၂ ခုပါဝင်ပါတယ်။

- `Ngrok` (အကောင့်လိုအပ်)
    
- `Cloudflared` (အကောင့်မလို)
    

🔹 Ngrok Defaulf:

```bash
./ngrok authtoken YOUR_TOKEN
```


---

### 4. Choose Phishing Page

CamPhish မှာ pre-built pages များ:

- Festival Wishing
    
- Live YouTube
    
- Google Survey Trick
    
- Custom URL Redirection
    

ဘယ်လို site လုပ်မလဲရွေးနိုင်ပါတယ်။

---

## ⚠️ သတိထားရမယ့်အချက်များ

### ✅ သုံးမယ့်အခါ:

- Own lab / test phone တွေမှာပဲ run ပြုလုပ်ပါ။
    
- Virtual machine, emulator သုံးပြီး စမ်းသပ်ပါ။
    
- Network မျိုးစုံမှာ tunnel ချိတ်ပြီး functionality စစ်ပါ။

---

## Troubleshooting Tips

- PNG black screen ဖြစ်နေလျှင် ⇒ မ victim က ဖုန်းမှာ **camera permission** မပေးရသေးတာဖြစ်နိုင်တယ်။
    
- Ngrok error ဖြစ်တယ် ⇒ Token မထည့်ရသေးတာ၊ မမှန်တာဖြစ်နိုင်တယ်။
    
- Link မဖြစ်ဘူး ⇒ Internet firewall တားထားတာဖြစ်နိုင်တယ်။
    

---

## 🌐 နောက်ထပ် Tools တွေလည်း စမ်းသင့်တယ်

- **SayCheese** (CamPhish နဲ့ဆင်တူ)
    
- **Zphisher** (Login phishing page ပိုများ)
    
- **Evilginx2** (Advanced phishing method - MITM style)
    

---
