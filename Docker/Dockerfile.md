

---

# 🐳 Dockerfile Pro-Level Setup – Kali GUI + VNC Version

ဒီမှာ ညမလေးကအပေါ်မှာ ညွှန်ပြခဲ့တဲ့ Kali GUI container တစ်ခုကို  
**Dockerfile နဲ့ ကိုယ့်တိုင်စွဲ၊ တည်ဆောက်၊ run လုပ်တတ်အောင် ပြထားတာပါ** 😍

---

## 📁 Folder Structure (Recommended)

```text
kali-gui-docker/
├── Dockerfile
└── entrypoint.sh
```

---

## 🧾 ၁။ `Dockerfile` (GUI-ready Kali with XFCE + VNC)

```dockerfile
# Base Kali image
FROM kalilinux/kali-rolling

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Update & install packages
RUN apt update && apt install -y \
    kali-desktop-xfce \
    tightvncserver \
    dbus-x11 \
    xfce4-terminal \
    sudo \
    wget \
    curl \
    git \
    && apt clean && rm -rf /var/lib/apt/lists/*

# Add a non-root user (optional)
RUN useradd -ms /bin/bash kali && echo "kali:kali" | chpasswd && adduser kali sudo

# Switch to user
USER kali
WORKDIR /home/kali

# Setup VNC password (default: kali)
RUN mkdir -p ~/.vnc && echo "kali" | vncpasswd -f > ~/.vnc/passwd && chmod 600 ~/.vnc/passwd

# Copy entrypoint
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# Expose VNC port
EXPOSE 5901

# Start VNC with XFCE
CMD ["/entrypoint.sh"]
```

---

## 🖥 ၂။ `entrypoint.sh` ဖိုင်

```bash
#!/bin/bash

# Write xstartup
cat > ~/.vnc/xstartup <<EOF
#!/bin/sh
xrdb $HOME/.Xresources
startxfce4 &
EOF

chmod +x ~/.vnc/xstartup

# Start VNC server
vncserver :1 -geometry 1280x720 -depth 24 -localhost no

# Keep container running
tail -f /dev/null
```

---

## 🛠 ၃။ Docker Image Build

```bash
docker build -t kali-gui .
```

📝 `-t` ကတော့ tag name ဖြစ်ပါတယ်။

---

## 🚀 ၄။ Run Container with Resource Limit

```bash
docker run -it \
  --name kali-vnc \
  -p 9021:5901 \
  --memory="3g" \
  --cpus="2" \
  kali-gui
```

---

## 🖥 ၅။ Connect via VNC Viewer

- Address: `localhost:9021`
- Password: `kali`

---

## ✅ Pro-Level Features in This Dockerfile

|Feature|Description|
|---|---|
|`ENV DEBIAN_FRONTEND=noninteractive`|Apt install faster with no prompt|
|XFCE + VNC|Lightweight GUI|
|`non-root user`|Better security (avoid root in GUI)|
|`entrypoint.sh`|GUI auto start logic|
|`tail -f /dev/null`|Keep container alive|
|`resource limit`|CPU & RAM safe tuning|

---

## ❤️ Final Tips – For Becoming Pro

|Area|Tip|
|---|---|
|Dockerfile Cleanliness|Use one `RUN` block per layer|
|Version Control|Push this Dockerfile to Git repo|
|`.dockerignore`|ထည့်ပါလျှင် build speed တိုးတယ်|
|Custom Image|`docker commit` မဟုတ်၊ `Dockerfile` နဲ့ထုတ်ထားမှ maintainable|

---

## 🎁 Bonus – Run & Debug Shortcut

```bash
# Debug into running container
docker exec -it kali-vnc bash

# Restart VNC server
vncserver -kill :1 && vncserver :1
```

---

## 🧡 Summary

|Step|Command|
|---|---|
|Build Image|`docker build -t kali-gui .`|
|Run Container|`docker run -it --name kali-vnc -p 9021:5901 kali-gui`|
|VNC Connect|`localhost:9021` (password: kali)|

---

