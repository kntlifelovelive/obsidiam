
`docker` CLI (Command Line Interface) 
--

## **Docker CLI နားလည်ဖို့အရေးကြီးဆုံး Command**

### 1️⃣ **Image (Download)**

```bash
docker pull <image-name>
```

ဥပမာ:

```bash
docker pull kalilinux/kali-rolling
```

➡️ DockerHub ကနေ Kali image ဆွဲတယ်။

---

### 2️⃣ **Container တစ်ခုကို Run လုပ်မယ်**

```bash
docker run [OPTIONS] <image-name>
```

ဥပမာ:

```bash
docker run -it kalilinux/kali-rolling
```

📌 **-it** ➜ Terminal input / interactive mode

📌 **--rm** ➜ Container run ပြီးရင် ဖျက်ပစ်မယ်

📌 **-d** ➜ Background မှာ run

📌 **--name** ➜ Container နာမည်ပေး

📌 **-p HOST:CONTAINER** ➜ Port forwarding

📌 **--network host** ➜ Host network ကို share မယ်

---

### 3️⃣ **Containers တက်နေတာ ကြည့်မယ်**

```bash
docker ps
```

📌 `-a` ဖြင့် အကုန် (တက် + မတက်တဲ့) ပြ

---

### 4️⃣ **Container ထဲ ဝင်မယ် (exec)**

```bash
docker exec -it <container-name or id> /bin/bash
```

ဥပမာ:

```bash
docker exec -it kali-container /bin/bash
```

---

### 5️⃣ **Container တစ်ခု ရပ်တယ် / ဖျက်တယ်**

```bash
docker stop <container-id or name>
docker rm <container-id or name>
```

---

### 6️⃣ **Installed Tool တွေနဲ့ Container ထဲက Image ပြန်သိမ်းချင်ရင် (Commit)**

```bash
docker commit <container-id or name> <new-image-name>
```

ဥပမာ:

```bash
docker commit 6d96b1a7 my-kali-tools
```

➡️ Kali ထဲ install လုပ်ထားတဲ့ tools အပြီး snapshot တင်တာ။

---

### 7️⃣ **Docker Image တွေကြည့်မယ်**

```bash
docker images
```

---

### 8️⃣ **Docker Container Logs ကြည့်မယ်**

```bash
docker logs <container-id or name>
```

---

### 9️⃣ **Docker Volume / Files mount**

```bash
docker run -v /host/path:/container/path <image>
```

📌 Read only လုပ်ချင်ရင်:

```bash
docker run -v /home/bubu/data:/data:ro <image>
```

---

## 🧠 **ဥပမာ CLI တစ်ခုရော ပြောပြမယ်နော်:**

```bash
sudo docker run -d \
  --name kali-vnc \
  -p 9020:8080 \
  -p 9021:5900 \
  -v /home/bubu/lab-data:/data:ro \
  iphoneintosh/kali-docker:latest
```

➡️ အကြောင်းအရာ:

|Part|Meaning|
|---|---|
|`-d`|Background run|
|`--name`|Container name = kali-vnc|
|`-p 9020:8080`|Kali VNC web → browser: `localhost:9020`|
|`-p 9021:5900`|Kali VNC viewer port|
|`-v /home/bubu/lab-data:/data:ro`|Host folder read-only mount to container|
|`iphoneintosh/kali-docker:latest`|Used image|

---

## 📌 နောက်ထပ် CLI option လိုချင်ရင်...

```bash
docker run --help
docker exec --help
docker build --help
```


---
