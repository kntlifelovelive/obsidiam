

# `inxi` 

`inxi` က command-line tool တစ်ခုပါ၊ system information ကို အကြမ်းဖျဉ်း/အသေးစိတ်ပြပေးနိုင်ပါတယ်။  
Linux system တွေမှာ GPU, CPU, RAM, kernel, display, network, audio, battery, power, hardware တွေကို debug/check လုပ်ရာမှာ အလွန်အသုံးဝင်ပါတယ်။


---

###  Installation

Arch-based (Kali Arch/Manjaro/Arch):

```bash
sudo pacman -S inxi
```

- Debian/Ubuntu-based:

```bash
sudo apt install inxi
```

- Version confirm:

```bash
inxi -V
```

---

##  Basic Usage

Hyprland debug info:

### a) System summary

```bash
inxi -F
```

- `-F` → Full system info  
- Output sample:


```
System:    Kernel: 6.5.8-arch1-1 x86_64 bits: 64
           Desktop: Hyprland  info: N/A Distro: Arch Linux
CPU:       Intel i7-10750H (12) @ 2.60GHz
GPU:       NVIDIA GeForce GTX 1660 Ti
Display:   X11: X.Org 1.21.1 drivers: nvidia
           resolution: 1920x1080
```

ဒီနဲ့ **desktop, kernel, GPU, driver, resolution** ကို တိုက်ရိုက်စစ်နိုင်ပါတယ်။

---

### b) Display / Monitor Info

```bash
inxi -G
```

- `-G` → Graphics/Display  
    Output sample:
    

```
Graphics:
  Device-1: NVIDIA TU116M [GeForce GTX 1660 Ti Mobile]
  driver: nvidia v: 525.78.01
  Display: x11 server: X.org 1.21.1 driver: nvidia
  resolution: 1920x1080~60Hz
```

Hyprland uses **Wayland**, so sometimes X11 info မရနိုင်ပါဘူး။ Wayland display info အတွက် `--display` အပြီးမှာ debug လုပ်ရပါမယ်:

```bash
inxi -Gxx
```

- `xx` → extra detail  
- Wayland framebuffer, render info, GPU driver version, OpenGL version တို့ကိုတွေ့နိုင်ပါတယ်။


---

### c) Input Devices (Keyboard, Mouse)

```bash
inxi -I
```

- `-I` → Input devices info  
    Example output:
    

```
Keyboard: HID System keyboard type: USB
Mouse: Logitech MX Master 3 type: USB
```

Hyprland မှာ hotkey/keyboard config ပြဿနာ ရှိရင် ဒီ command နဲ့ device detect ဖြစ်မလား စစ်ရပါတယ်။

---

### d) Power / Battery (Laptop)

```bash
inxi -B
```

- `-B` → Battery info  
- Example:

```
Battery:
  ID-1: BAT0 charge: 50.0 Wh (100%) condition: 50.0/50.0 Wh
  status: Discharging
```

Hyprland + laptop tuning (auto-governor, brightness change) စမ်းချင်ရင် ဒီ info က အရမ်းအသုံးဝင်ပါတယ်။

---

### e) Kernel / Modules / Driver

```bash
inxi -Sxxx
```

- `-S` → System info
- `xxx` → Extra verbose, driver/module info  Output example:

```
Kernel: 6.5.8-arch1-1 x86_64
Driver: nvidia
Modules: nvidia, nvidia_modeset, nvidia_uvm
```

Hyprland GPU/driver problem troubleshoot လုပ်ရာမှာ အရေးကြီးပါတယ်။

---

##  Practical Debug Scenarios (Hyprland)

### Scenario 1 – GPU problem

**Problem:** Hyprland rendering lag, compositor crash, or black screen

**Command:**

```bash
inxi -Gxx
```

**Check:**

- Driver installed? (`driver: nvidia`)
- GPU detected? (`Device-1`)
- OpenGL version?
- Wayland support ok?

**Fix:**

- Driver update/reinstall
- `nvidia-drm.modeset=1` in kernel boot params for Wayland

---

### Scenario 2 – Multiple Monitors

**Problem:** Monitor not detected

**Command:**

```bash
inxi -Gxx
```

- Check `Display-1`, `Display-2`
- Check resolution, refresh rate


**Fix:**

- Hyprland config: `monitor=eDP-1,1920x1080@60`
- GPU driver problem? `inxi -G` confirms


---

### Scenario 3 – Keyboard / Hotkey problem

**Problem:** Keybindings not working in Hyprland

**Command:**

```bash
inxi -I
```

- Confirm input devices detected
- Device name must match Hyprland config

---

### Scenario 4 – Power / Battery tuning

**Problem:** Laptop doesn't auto-adjust CPU governor on plug/unplug

**Command:**

```bash
inxi -B
inxi -C
```

- `-C` → CPU info, current governor
- `-B` → Battery status

Check governor status when plugging/unplugging charger:

```bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

`inxi` က quick overview ပေးပြီး Hyprland automation testing လုပ်ဖို့ အဆင်ပြေပါတယ်။

---

## Advanced: Full Debug Command

```bash
inxi -Fxxxrz
```

- `-F` → Full info
- `xxx` → extra detail
- `r` → refresh rate
- `z` → hide serial numbers/passwords

**Output**: CPU, GPU, Driver, Monitors, Input, Memory, Kernel, Distro, Audio, Battery, Network

Hyprland debug နဲ့ log analysis အတွက် အပြည့်စုံဆုံး command ဖြစ်ပါတယ်။

---

- Hyprland compositor crash / render lag → `inxi -Gxx`
- Keybinding/device issue → `inxi -I`
- Monitor issue → `inxi -G`
- Laptop battery/governor → `inxi -B -C`


---


---



##  **System Summary**

**Command:**

```bash
inxi -F
```

**Simulated Output:**

```
System:    Kernel: 6.5.8-arch1-1 x86_64 bits: 64
           Desktop: Hyprland  info: N/A Distro: Arch Linux
CPU:       Intel i7-10750H (12) @ 2.60GHz
Memory:    16GB RAM
GPU:       NVIDIA GeForce GTX 1660 Ti
Display:   resolution: 1920x1080@60Hz
```

**Checkpoints:**

- Kernel version (Wayland friendly)
- Hyprland desktop detected
- CPU/GPU info correct
- Memory OK
- Display resolution correct


---

## **Graphics / GPU Debug**

**Command:**

```bash
inxi -Gxx
```

**Simulated Output:**

```
Graphics:
  Device-1: NVIDIA TU116M [GeForce GTX 1660 Ti Mobile]
  driver: nvidia v: 525.78.01
  Display: wayland server: Hyprland driver: nvidia
  resolution: 1920x1080~60Hz
  OpenGL: 4.6 NVIDIA 525.78.01
```

**Checkpoints:**

- GPU device detected? 
- Driver installed and correct? 
- Wayland server info correct? 
- OpenGL version compatible? 

**Debug Tip**

- GPU lag/black screen → check `nvidia-drm.modeset=1` in kernel boot params
- Multiple monitors → check `Display: Display-1, Display-2`
- Missing driver → reinstall `nvidia` package


---

## **Input Devices Debug**

**Command:**

```bash
inxi -I
```

**Simulated Output:**

```
Keyboard: HID System keyboard type: USB
Mouse: Logitech MX Master 3 type: USB
Touchpad: ELAN1200 type: internal
```

**Checkpoints:**

- Keyboard detected? 
- Mouse detected? 
- Touchpad detected? 

**Debug Tips:**

- Keybindings not working → confirm device name matches `hyprland.conf`
- Multiple keyboards/mice → verify correct `input` section in config


---

## **Battery & CPU Governor Debug (Laptop)**

**Commands:**

```bash
inxi -B -C
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

**Simulated Output:**

```
Battery:
  ID-1: BAT0 charge: 50.0 Wh (100%) condition: 50.0/50.0 Wh
  status: Discharging

CPU:
  Core: 6x Intel i7-10750H @ 2.60GHz
  Current Governor: powersave
```

**Checkpoints:**

- Battery detected? 
- Charge level correct? 
- CPU governor correct? 

**Debug Tips**

- Auto governor script not working → check `/sys/devices/.../scaling_governor` changes on plug/unplug
- Brightness automation → verify `/sys/class/backlight` path


---

## **Full Debug / All Info**

**Command**

```bash
inxi -Fxxxrz
```

**Simulated Output:**

```
System:
  Host: hyprbook Kernel: 6.5.8-arch1-1 x86_64 bits: 64
  Distro: Arch Linux Desktop: Hyprland
CPU:
  Intel i7-10750H (6 cores, 12 threads) @ 2.6GHz
Memory:
  16GB RAM
Graphics:
  NVIDIA GeForce GTX 1660 Ti Mobile
  Driver: nvidia v525.78.01 Wayland: Hyprland
  OpenGL: 4.6
Monitors:
  eDP-1: 1920x1080@60Hz
Input Devices:
  Keyboard: HID System
  Mouse: Logitech MX Master 3
Battery:
  50Wh, Discharging
Network:
  Wi-Fi: Intel AX200
Audio:
  NVIDIA Audio, Intel HD Audio
```

**Checkpoints**

- Full system overview 
- GPU, display, input, battery, network, audio, kernel all checkable
- Perfect for crash/lag/hotkey debug

---

### **Practical Debug Workflow Summary**

1. `inxi -F` → Quick overview, check desktop/kernel/GPU/Memory
2. `inxi -Gxx` → GPU & display debug (Wayland vs X11, OpenGL, driver)
3. `inxi -I` → Input devices debug (keybinding issues)
4. `inxi -B -C` → Laptop battery + CPU governor automation
5. `inxi -Fxxxrz` → Full debug, system crash analysis, multiple monitors, audio, network



## **Real Log Collection**

### a) GPU / Wayland / Compositor Logs

Hyprland log ကို collect လုပ်ဖို့:

```bash
journalctl --user -u hyprland -b
```

- `--user` → user service
- `-u hyprland` → Hyprland service
- `-b` → current boot

**Simulated Output Example:**

```
[INFO] Initializing Hyprland...
[DEBUG] Loaded monitor: eDP-1 1920x1080@60Hz
[ERROR] Failed to initialize NVIDIA EGL backend
[INFO] Keyboard: HID System
[INFO] Mouse: Logitech MX Master 3
```

**Checkpoints:**

- Monitor detected 
- NVIDIA driver backend error ❌ → driver reinstall or modeset fix
- Input devices loaded 

---

### b) Wayland Session Info

```bash
loginctl show-session $(loginctl | grep $(whoami) | awk '{print $1}') -p Type
```

Output:

```
Type=wayland
```

- Confirm session is Wayland, not X11 → GPU/driver debugging depends on this

---

### c) Input Device Debug

```bash
libinput list-devices
```

Simulated Output:

```
Device:           System Keyboard
Kernel:           /dev/input/event3
Group:            3
Capabilities:     keyboard
```

- Keybinding issue → check if Hyprland config `input` section matches this device name
    

---

### d) Monitor / Multi-Display Debug

```bash
swaymsg -t get_outputs
```

Simulated Output:

```
Output eDP-1:
  active: yes
  resolution: 1920x1080
Output HDMI-A-1:
  active: no
  resolution: 2560x1440
```

- Check if Hyprland detects all monitors correctly
- If inactive → cable, driver, or config issue

---

### e) CPU Governor / Battery Log

```bash
watch -n 2 cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
watch -n 5 inxi -B
```

- `watch` → live monitoring
- CPU governor auto-change not working → script or ACPI event problem
- Battery → plug/unplug event test

---

## **Error Analysis Example**

### Scenario: Hyprland lagging, black screen after NVIDIA update

**Steps:**

1. `inxi -Gxx` → GPU detected? 
2. `journalctl --user -u hyprland -b` → Check for `[ERROR] Failed to initialize NVIDIA EGL backend` 
3. `nvidia-smi` → Confirm NVIDIA driver active
4. `cat /sys/module/nvidia_drm/parameters/modeset` → Must be `Y`
5. Fix → add `nvidia-drm.modeset=1` to kernel boot params → reboot → test with `inxi -Gxx`

**Outcome:** GPU detected, Wayland backend working, lag gone

---

### Scenario: Hotkey not working

1. `inxi -I` → Keyboard detected? 
2. `libinput list-devices` → Device name matches Hyprland config? 
3. Hyprland config check → `bind = $mod, Return, exec, alacritty`
4. Test → `hyprctl reload`
5. If still not working → log `journalctl --user -u hyprland` → check errors


---

### Scenario: Monitor not detected

1. `inxi -Gxx` → GPU sees multiple outputs? 
2. `swaymsg -t get_outputs` → Check output status
3. If inactive → `xrandr` not useful in Wayland → check Hyprland config:


```ini
monitor=HDMI-A-1,2560x1440@144,0,0,1
```

4. Reload → `hyprctl reload`
    
5. Check log → `journalctl --user -u hyprland`
    

---

## **Recommended Debug Command Set**

|Purpose|Command|
|---|---|
|Full system info|`inxi -Fxxxrz`|
|GPU / Display|`inxi -Gxx`|
|Input devices|`inxi -I`|
|Battery / CPU|`inxi -B -C`|
|Hyprland logs|`journalctl --user -u hyprland -b`|
|Wayland session|`loginctl show-session $(loginctl|
|Monitor status|`swaymsg -t get_outputs`|
|Live CPU governor|`watch -n 2 cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor`|

---


- Always start with `inxi` overview → check hardware detection
    
- Then check logs (`journalctl`) → find driver/compositor errors
    
- Input & monitors → `libinput` & `swaymsg` → config fix
    
- Power & governor → `/sys/devices/...` & scripts → automation
    

---
