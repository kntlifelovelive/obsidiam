---

---


---

###  **🛠 Install setup for Arch linux Hyprland configuration**
**Screenshot Tool Install**  

- `grim + slurp` → Hyprland + Wayland of lightweight tool .
- `grimblast` → hyprland-user package Easy Usage. 

```bash 
sudo pacman -S grim slurp wl-clipboard
yay -S grimblast  # AUR Package Manager for install command 

```

###  **Test Command**  for terminal 
- Basic screenshot 

```bash 
grim ~/Pictures/screenshot.png

```

- Region select (mouse of drag)

```bash 
grim -g "$(slurp)" ~/Pictures/screenshot.png

```

- grimblast easy 

```bash 
grimblast copysave area ~/Pictures/screenshot.png

```

*Note*  *(အဲ့မှာ `area` ဆိုတာ region select UI ပေါ်လာပြီး drag လုပ်နိုင်မယ်)*


### Hyprland Keybinding

- **Keybinding configuration**

```bash 

# ------------------------------
# Screenshot Keybindings (No $mainMod)
# ------------------------------

# 1️⃣ PrintScreen = Select Area & Save to ~/Pictures
bind = , Print, exec, grimblast copysave area ~/Pictures/screenshots/-$(date +%Y-%m-%d_%H-%M-%S).png

# 2️⃣ Shift+PrintScreen = Fullscreen Screenshot & Save
bind = SHIFT, Print, exec, grimblast copysave screen ~/Pictures/screenshots/-$(date +%Y-%m-%d_%H-%M-%S).png

# 3️⃣ Ctrl+PrintScreen = Select Area & Copy to Clipboard (no file saved)
bind = CTRL, Print, exec, grimblast copy area

# 4️⃣ Alt+PrintScreen = Active Window Screenshot & Save
bind = ALT, Print, exec, grimblast copysave active ~/Pictures/screenshots/-$(date +%Y-%m-%d_%H-%M-%S).png

```

---

### Troubleshooting Checklist 

```bash 
which grimblast

which slurp

sudo pacman -S slurp grim wl-clipboard

```

#### Test manually first

```bash

grimblast copysave area ~/Pictures/test.png

```

---

## 🎥 Hyprland Video Screen Capture Setup

**1. Package Install**



- Arch  Wayland  Hyprland  `wf-recorder` install 

```bash

sudo pacman -S wf-recorder slurp

```

**2.Basic Command (Manual Test)**

```bash 

wf-recorder -g "$(slurp)" -f ~/Videos/screencast/-$(date +%Y-%m-%d_%H-%M-%S).mp4

```

 - Cursor ✚ on → region select 
- Recording start လုပ်သွားမယ် (Terminal minimize )
- **Ctrl+C** ==> stop 
- File ကို `~/Videos`  inside save file Video Screencast 🎬

### Install Checklist
```bash 
sudo pacman -S wf-recorder slurp pipewire pipewire-pulse wl-clipboard

```

### System Sound Source 
- PipeWire + PulseAudio install check Package:

```bash 
pactl list short sources

```

- *2. Output Example:* 
```bash

╭─[ 🌺 ]-[Videos]  📂 24 
╰─> pactl list short sources 
56	alsa_output.pci-0000_00_1f.3.analog-stereo.monitor	PipeWire	s32le 2ch 48000Hz	SUSPENDED
57	alsa_input.pci-0000_00_1f.3.analog-stereo	PipeWire	s32le 2ch 48000Hz	SUSPENDED
90	bluez_output.41_42_94_97_08_57.1.monitor	PipeWire	s16le 2ch 48000Hz	RUNNING

```


---



### 3. 🎥 **Hyprland Screen Recording Config (Final Version)**

**~/.config/your - configuration file add**

### Final Config Keybinding 

```bash 

# ========================
# 🎥 Video Recording
# ========================

# 1️⃣ Region Select + System Sound (Bluetooth / Speakers)
bind = , F10, exec, wf-recorder -g "$(slurp)" -a bluez_output.41_42_94_97_08_57.1.monitor -f ~/Videos/record-system-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🎥 Recording Started (System Sound)"

# 2️⃣ Region Select + Microphone (Voice)
bind = SHIFT, F10, exec, wf-recorder -g "$(slurp)" -a alsa_input.pci-0000_00_1f.3.analog-stereo -f ~/Videos/record-mic-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🎤 Recording Started (Mic)"

# 3️⃣ Fullscreen + System Sound
bind = , F9, exec, wf-recorder -a bluez_output.41_42_94_97_08_57.1.monitor -f ~/Videos/fullscreen-system-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🖥️ Recording Fullscreen (System Sound)"

# 4️⃣ Fullscreen + Microphone
bind = SHIFT, F9, exec, wf-recorder -a alsa_input.pci-0000_00_1f.3.analog-stereo -f ~/Videos/fullscreen-mic-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🖥️ Recording Fullscreen (Mic)"

# 5️⃣ Stop Recording
bind = , F11, exec, pkill -SIGINT wf-recorder && notify-send "⏹ Recording Stopped" "Saved to ~/Videos"

```

## Trick

- **F10** → Region Select + System Sound (Bluetooth / Speaker sound only)
- **Shift+F10** → Region Select + Microphone
- **F9** → Fullscreen + System Sound
- **Shift+F9** → Fullscreen + Microphone
- **F11** → Stop Recording

---

