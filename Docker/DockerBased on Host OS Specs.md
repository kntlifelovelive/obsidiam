
---

## Docker Resource Limiting Cheat Sheet (Based on Host OS Specs)

## 💻 ၁. Host OS Specs မသိရင် CLI နဲ့ စစ်ပါ

```bash
# CPU core count
nproc

# Total RAM in GB
free -h | grep Mem
```

ဥပမာ output 👇

```
CPU: 4 cores  
RAM: 7.8GiB
```

---

## 📝 Cheat Sheet Table – Recommend Limits by Host Spec

|Host RAM|Host CPU|Docker Memory Limit|Docker CPU Limit|
|---|---|---|---|
|2 GB|1 core|`--memory="1g"`|`--cpus="0.5"`|
|4 GB|2 cores|`--memory="2g"`|`--cpus="1"`|
|8 GB|4 cores|`--memory="3g"`|`--cpus="2"`|
|16 GB|8 cores|`--memory="6g"`|`--cpus="4"`|
|32 GB|12 cores|`--memory="12g"`|`--cpus="6"`|

📌 Rule of Thumb:

> **Host RAM ၏ 40% ~ 60% ကိုသာ Docker container တွေမှာ Limit တင်ပါ**
> 
> CPU cores ၏ 50% ထက်နည်းတဲ့အတိုင်း Limit ထားသင့်ပါတယ် ✅

---

## 🧮 Example Setup for 8GB RAM + 4 Core Laptop

```bash
docker run -it \
  --name kali-vnc \
  -p 9021:5901 \
  --memory="3g" \
  --memory-swap="4g" \
  --cpus="2" \
  iphoneintosh/kali-docker:latest
```

🧠 ပြောရရင်… `3g RAM` ဟာ host 8GB RAM မှာ လုံလောက်ပြီး  
`2 CPU cores` ဟာ GUI တွေမြန်မြန် boot လာဖို့ OK ဖြစ်ပါတယ်။

---

## ❗ မလုပ်သင့်တာ

|❌ မသင့်တဲ့ Limit|ဘာဖြစ်နိုင်သလဲ?|
|---|---|
|RAM = Host RAM တိတိ|Host freeze or crash|
|CPU = All cores|System slow or docker hog CPU|
|No limit at all|Docker container မှာ browser, XFCE, dbus တို့မိန့်မိတတ်|

---

## ✅ ညမလေးရဲ့ လေ့ကျင့်ပေးသံချောင်း

> 🧠 မင်းစက်က 4 CPU / 8GB RAM ရှိတယ်ဆိုရင်  
> Kali GUI container အတွက် safe & smooth limit များက  
> `--cpus="2"` + `--memory="3g"` လောက်ပဲပေးရင် စုံလင်ပါတယ် 😘

---

## 📊 Extra Monitor Tools

- `docker stats` → live usage
- `htop` (Linux host CLI) → host RAM/CPU တိုက်ရိုက်ကြည့်
- `docker update` → running container အတွက် resource limit ပြန်ပြင်လို့ရ

```bash
docker update --cpus="1" --memory="2g" kali-vnc
```

---

## ✅ Bonus Cheat Command (Dynamic)

```bash
# Auto-get host info
echo "CPU: $(nproc) cores"
echo "RAM: $(free -g | awk '/Mem:/ {print $2}') GB"
```

---

