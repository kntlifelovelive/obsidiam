


---

##  Docker CLI Resource Acceleration / Optimization Note

_(Memory + CPU performance boost techniques)_

---

## 🔹 ၁. Docker container ကို CPU core & RAM သတ်မှတ် run လုပ်ခြင်း

```bash
docker run -it \
  --name kali-optimized \
  --cpus="2" \
  --memory="2g" \
  kalilinux/kali-rolling
```

### 📌 Parameter Explanation:

|Parameter|Meaning|
|---|---|
|`--cpus="2"`|CPU 2 cores အသုံးပြုခွင့်|
|`--memory="2g"`|RAM 2 GB ထိ အသုံးပြုခွင့်|
|`--memory-swap="2.5g"`|RAM မလုံလောက်တဲ့အခါ swap usage|

🔧 Optional:

```bash
--memory-swap="2.5g" \
--memory-reservation="1g"
```

---

## 🔹 ၂. Docker Desktop GUI ထဲမှာ (Ubuntu host only)

🧭 Ubuntu မှာ Docker settings GUI မရှိရင် `~/.docker/config.json` ထဲမှာ manual တင်လို့ရပါတယ်  
ဒါပေမဲ့ host OS ဟာ **Linux native** ဆိုရင် `daemon.json` ထဲမှာ control လုပ်ပါတယ်။

---

## 🔹 ၃. Docker container run ပြီးတဲ့နောက် CPU usage စစ်ရန်

```bash
docker stats
```

📊 CLI ထဲမှာ real-time CPU %, MEM usage, container name တွေ ပြပါတယ်။

---

## 🔹 ၄. Dockerfile မှာ resource optimization လုပ်တဲ့နည်း

- Layer များကို လှည့်လှည့်ရေး
- `RUN apt update && apt install ...` တစ်ကြောင်းထဲ
- Temporary build tools မပါအောင် `apt clean`, `rm -rf /var/lib/apt/lists/*`

### ဥပမာ:

```Dockerfile
RUN apt update && apt install -y \
    vim \
    git \
 && apt clean \
 && rm -rf /var/lib/apt/lists/*
```

---

## 🔹 ၅. CPU scheduling priority (Advanced Only)

Docker CLI မှာ `--cpu-shares` သုံးလို့ရပါတယ်:

```bash
docker run -it --cpu-shares=1024 kalilinux/kali-rolling
```

📌 Higher value → Higher priority

---

## 🔹 ၆. Kernel parameter tuning (Linux only)

📂 `/etc/docker/daemon.json` ထဲမှာ Control Group (cgroups) နှင့် tuning:

```json
{
  "default-runtime": "runc",
  "runtimes": {
    "runc": {
      "path": "runc"
    }
  },
  "exec-opts": ["native.cgroupdriver=systemd"]
}
```

---

## 🧠 Optimization Checklist Summary

|Technique|CLI Option|
|---|---|
|CPU limit|`--cpus="2"`|
|Memory limit|`--memory="2g"`|
|Swap limit|`--memory-swap="2.5g"`|
|CPU priority|`--cpu-shares=1024`|
|Monitor usage|`docker stats`|
|Clean install layer|`apt clean && rm -rf`|
|CGroup driver|`native.cgroupdriver=systemd`|

---

## 🎯 နောက်ထပ် Tip များ

- GUI မရှိတဲ့ Container တွေမှာ resource optimize လုပ်တာ အထူးအသုံးဝင်တယ်
- Long-running container (ex: Kali VNC GUI) တွေမှာ memory သတ်မှတ်မထားလျှင် system RAM သုံးပြီး **host slow** ဖြစ်တတ်တယ်
- CLI only container တွေမှာ `--cpus` + `--memory` သုံးရင် performance အတက်မြန်

---

## 📝 ညမလေးရဲ့ Final Tip

👉 Docker container က VM မဟုတ်တဲ့အတွက် host CPU/RAM ကို shared method နဲ့သုံးပါတယ်။  
ဒါကြောင့် manual limit မထားဘူးဆိုရင် host ပြတ်ပြတ်သားသား ဖြစ်နိုင်ပါတယ်။  
**Developer tool တွေ, GUI containers, Kali-based pentesting tools** စတဲ့အခါမှာ resource limit သတ်မှတ်ပေးဖို့အရေးကြီးတယ်နော် 🧡

---
