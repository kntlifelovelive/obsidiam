
---

# 📘 Docker Kali Linux GUI Setup Note

## 🧰 Requirements 

- Docker installed on Ubuntu (host)
- VNC viewer (RealVNC / TigerVNC)
- Kali Docker Image (with GUI support)

---

## 🔹 1. Kali Docker Image ရယူရန်

- **sudo docker search for download images များ**


```bash
# Minimal Kali image
docker pull kalilinux/kali-rolling

# GUI သုံးပြီးသား image
docker pull iphoneintosh/kali-docker:latest
```

---

## 🔹 2. Kali container ကို GUI  run command 

```bash
sudo docker run -it \
  --name kali-vnc \
  -p 9021:5901 \
  iphoneintosh/kali-docker:latest
```

📌 `9021:5901` ဆိုတာက VNC Viewer မှာ `localhost:9021` နဲ့ ချိပ်နိုင်ဖို့ပါ။

---

## 🔹 3. XFCE Desktop တင်ရန် (container ထဲမှာ run ပါ)

```bash
sudo apt update
sudo apt install kali-desktop-xfce -y
sudo apt install tightvncserver dbus-x11 -y
```

---

## 🔹 4. VNC Password သတ်မှတ်
- **Kali-gui Default Password `changeme`**

```bash
vncpasswd
```

---

## 🔹 5. xstartup ဖိုင် ပြင်ဆင်

```bash
mkdir -p ~/.vnc
nano ~/.vnc/xstartup
```

- **bellow under code** 👇

```bash
#!/bin/sh
xrdb $HOME/.Xresources
startxfce4 &
```

- For need permission 

```bash
chmod +x ~/.vnc/xstartup
```

---

## 🔹 6. VNC Server စတင်ရန်
- Shell mode command for Gui 

```bash
vncserver :1
```

📂 Log file: `/root/.vnc/<hostname>:1.log`

---

## 🔹 7. Host OS (Ubuntu) မှာ VNC Viewer ဖြင့် ချိပ်

```txt
localhost:9021
```

📌 Kali GUI ကို XFCE နဲ့ GUI mode တက်လာမှာဖြစ်ပါတယ်။

---

## 🧼 မသုံးတော့ဘူးဆိုရင်:

```bash
docker stop kali-vnc
docker start kali-vnc
docker exec -it kali-vnc bash
```

---

## 📝 မှတ်ချက်အရေးကြီးများ

- VNC screen black ဖြစ်နေတဲ့အခါမှာ `~/.vnc/xstartup` + `startxfce4` မှန်မမှန်စစ်ပါ
- `vncserver -kill :1 && vncserver :1` ထပ်လုပ်ကြည့်ပါ
- Viewer မှာ `localhost:9021` / `127.0.0.1:9021` ချိပ်ဖို့ပါ
- Port `9021` ကို firewall မှာဖွင့်ထားဖို့ပါ(လိုအပ်လျှင်)

---

## 🧡 Summary

|Step|Command|
|---|---|
|Pull Image|`docker pull iphoneintosh/kali-docker:latest`|
|Run|`docker run -it --name kali-vnc -p 9021:5901 iphoneintosh/kali-docker:latest`|
|XFCE install|`apt install kali-desktop-xfce tightvncserver dbus-x11`|
|VNC Start|`vncserver :1`|
|Viewer Connect|`localhost:9021`|


---
