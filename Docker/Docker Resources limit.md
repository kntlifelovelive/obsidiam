
---


> **Long-running container (e.g., Kali VNC GUI)** တွေအတွက်  
> Host system မနှေးအောင် **memory + CPU limits** ပါတစ်ချိန်တည်းသတ်မှတ်ထားတဲ့  
> Full Docker Command + Final Resource Limiting Guide** ကို အတိအကျပြသပေးလိုက်ပြီပါလား 💡

---

## Docker GUI Container + Resource Limit Command (For Long-Running)

```bash
docker run -it \
  --name kali-vnc \
  -p 9021:5901 \
  --memory="2g" \
  --memory-swap="2.5g" \
  --cpus="1.5" \
  --cpu-shares="1024" \
  iphoneintosh/kali-docker:latest
```

---

## 📌 Parameters Explanation (နားလည်ဖို့အတွက်)

|Flag|အဓိပ္ပါယ်|အကြံပြု|
|---|---|---|
|`--memory="2g"`|Container ကို 2 GB RAM ထက်မပိုခွင့်မပြုပါ|✅ Required|
|`--memory-swap="2.5g"`|RAM မလုံလောက်လျှင် swap ထဲသွားမယ်|✅ Optional|
|`--cpus="1.5"`|1.5 CPU cores သာသုံးခွင့်ရှိ|✅ Host CPU usage နည်းစေမယ်|
|`--cpu-shares="1024"`|Scheduling priority|✅ Default: 1024 (မြင့်လိုသလောက်တင်)|
|`-p 9021:5901`|VNC GUI ပြသရန် port mapping|✅ Required|

---

## 🔎 Resource Usage ကို Live စစ်ချင်ရင်

```bash
docker stats kali-vnc
```

📊 Output:

```
CONTAINER ID   NAME       CPU %     MEM USAGE / LIMIT     MEM %   ...
a1b2c3...      kali-vnc   35.22%    1.2GiB / 2GiB          60%
```

---

## ✅ Practical Use Case (VNC GUI Kali container)

👉 တစ်ကြိမ်တင်ပြီး GUI နဲ့ RealVNC တပ်ပြီးထားတာဆို...

- 🔸 RAM ကို မသတ်မှတ်ဘူးဆို ➜ XFCE, background service, browser ထဲက RAM usage ကြီးတတ်တယ်
- 🔸 Host OS (Ubuntu) အထိ ပြတ်ပြတ်သားသား ဖြစ်တတ်တယ်

ဒါကြောင့် resource limit သတ်မှတ်ထားတဲ့ command က host stability အတွက်အရေးကြီးတယ်နော် 💯

---

# 📝 Final Tip Summary (Resource-limited Docker)

## ✅ Always use resource limits for:

- GUI containers (e.g. Kali XFCE + VNC)
- Browsers, Heavy Tools inside container
- Low-RAM laptops/PC (2GB~8GB)

## 🔒 Recommended Limits:

|Resource|Setting|
|---|---|
|RAM|`--memory="2g"`|
|SWAP|`--memory-swap="2.5g"`|
|CPU|`--cpus="1.5"`|
|CPU Priority|`--cpu-shares="1024"`|

---

## 🧪 Pro-Level Add-ons

🧠 Add alias in your shell for auto-limiting run:

```bash
alias run_kali_vnc='docker run -it --name kali-vnc -p 9021:5901 --memory=2g --memory-swap=2.5g --cpus=1.5 iphoneintosh/kali-docker:latest'
```

📂 `~/.bashrc` or `~/.zshrc` ထဲထည့်နိုင်ပါတယ်။

---

