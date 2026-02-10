
---

## Audio (PipeWire / PulseAudio / ALSA)

#### Audio server check

```bash
pactl info | grep "Server Name"
```

- `PipeWire` / `PulseAudio` ဆိုတာမြင်ရမယ်

### Audio device list

```bash
pactl list short sinks
pactl list short sources
```

### ALSA level

```bash
aplay -l
arecord -l
```

### PipeWire status (Arch default)

```bash
systemctl --user status pipewire
systemctl --user status wireplumber
```

---

## Bluetooth (Audio / Device)

### Bluetooth service run 

```bash
systemctl status bluetooth
```

### Bluetooth controller info

```bash
bluetoothctl show
```

### Paired devices

```bash
bluetoothctl paired-devices
```

### Connected devices

```bash
bluetoothctl devices Connected
```

### Bluetooth audio codec check (PipeWire)

```bash
pactl list cards | grep -i bluez -A20
```

-  SBC / AAC / LDAC / aptX စတဲ့ codec တွေပါ မြင်နိုင်တယ်

---

## Package Management (pacman)

### Installed packages list

```bash
pacman -Q
```

### Explicit install (ကိုယ်တိုင် install)

```bash
pacman -Qe
```

### Dependency only

```bash
pacman -Qd
```

### Orphan packages (ဖျက်လို့ရတဲ့ deps)

```bash
pacman -Qtdq
```

### Package info detail

```bash
pacman -Qi pipewire
```

### Package ဘယ် file တွေ ထုတ်ထားလဲ

```bash
pacman -Ql bluez
```

### File တစ်ခု ဘယ် package ကလာလဲ

```bash
pacman -Qo /usr/bin/bluetoothctl
or 
pacman -Qo bluetoothctl

terminal output =================
/usr/bin/bluetoothctl is owned by bluez-utils 5.85-1


pacman -Qo hyprctl

terminal output ===================
/usr/bin/hyprctl is owned by hyprland 0.53.3-1


```

---

## USB / PCI Hardware

### USB devices

```bash
lsusb
```

### PCI devices (audio / network)

```bash
lspci
```

### Audio device ကို filter

```bash
lspci | grep -i audio
```

---

##  System / Kernel / Driver

### Kernel info

```bash
uname -a
```

### Loaded modules

```bash
lsmod
```

### Bluetooth driver check

```bash
lsmod | grep bt
```

### dmesg (hardware error / log)

```bash
dmesg | grep -i blue
dmesg | grep -i audio
```

---

## Services (systemd)

### Running services

```bash
systemctl list-units --type=service --state=running
```

### Failed services

```bash
systemctl --failed
```

### User services (PipeWire, Hyprland stuff)

```bash
systemctl --user list-units --state=running
```

---
---
## Hyprland + Arch

Bluetooth audio မထွက်ရင် စစ်ရမယ့် order 

1️⃣ `systemctl status bluetooth`  
2️⃣ `pactl info` (PipeWire?)  
3️⃣ `pactl list cards`  
4️⃣ `bluetoothctl devices Connected`  
5️⃣ `journalctl -u bluetooth`

---
