

**MPV** ကတော့ **open-source, lightweight, and highly customizable media player** တစ်ခုဖြစ်ပါတယ်။ ဗီဒီယို၊ သီချင်းတွေအတွက် CLI (Command-Line Interface) နှင့် GUI (Graphical User Interface) နှစ်မျိုးလုံးကို အသုံးပြုနိုင်ပါတယ်။ MPV ဟာ **MPlayer** နှင့် **MPlayer2** အခြေခံပြီး အဆင့်မြှင့်ထားတဲ့ လုပ်ဆောင်ချက်တွေ ပါဝင်ပါတယ်။

* * *

## **MPV အကြောင်း**

1.  **တော်လှန်ဖွဲ့စည်းမှု**  
    MPV ဟာ GUI interface တစ်ခုမရှိဘဲ **Command-line** မှတစ်ဆင့်ဖွင့်နိုင်ပါတယ်။ GUI frontend မလိုအပ်တဲ့အတွက် လုပ်ဆောင်ချက် အမြန်မြန်လုပ်ဆောင်နိုင်ပါတယ်။
    
2.  **Lightweight**  
    အခြား media players တွေထက် resource အသုံးချမှုနည်းပြီး **low CPU & memory usage** နဲ့လည်း အရမ်းစွမ်းဆောင်ရည်ကောင်းပါတယ်။
    
3.  **High-quality Playback**  
    MPV မှာ **hardware acceleration** နဲ့ **video quality enhancement** တွေဖြင့် resolution, filter, HDR အသုံးပြုနိုင်ပါတယ်။
    
4.  **Customization**  
    MPV ရဲ့ **config files** မှတစ်ဆင့် playback, shortcuts, audio/video settings တွေကို စိတ်ကြိုက်ပြုလုပ်နိုင်ပါတယ်။
    
5.  **Streaming Support**  
    Online video URLs, YouTube-dl နဲ့ပေါင်းစပ်ပြီး **YouTube, Vimeo** စတဲ့ streaming videos တွေကိုလည်း ထောက်ပံ့ဖွင့်နိုင်ပါတယ်။
    

* * *

## **Installation**

Linux မှာ MPV ကို အောက်ပါအတိုင်း တပ်ဆင်နိုင်ပါတယ်။

### **Debian/Ubuntu/Kali**

```bash
sudo apt update
sudo apt install mpv
```

### **Arch Linux**

```bash
sudo pacman -S mpv
```

### **Fedora**

```bash
sudo dnf install mpv
```

* * *

## **MPV Basic Usage (Terminal CLI)**

### **1\. Media ဖွင့်ခြင်း**

```bash
mpv /path/to/file.mp4
```

### **2\. YouTube Video ဖွင့်ခြင်း**

MPV ရဲ့ YouTube-dl integration ကိုသုံးပြီး YouTube URL တွေကိုဖွင့်နိုင်ပါတယ်။

```bash
mpv https://www.youtube.com/watch?v=example
```

### **3\. Loop Playback**

ဖွင့်တဲ့ File ကို ထပ်ခါထပ်ခါ Loop ပြန်ဖွင့်ဖို့

```bash
mpv --loop /path/to/song.mp3
```

### **4\. Audio Only Mode**

Video File တစ်ခုကို Audio အနေနဲ့ဖွင့်ပါ။

```bash
mpv --no-video /path/to/video.mp4
```

### **5\. Volume Control**

Volume ကို % အနေနဲ့ ပြုလုပ်နိုင်ပါတယ်။

```bash
mpv --volume=50 /path/to/file.mp3
```

### **6\. Subtitle Support**

Subtitles file ကို ပါစေချင်ရင်

```bash
mpv --sub-file=subtitle.srt /path/to/video.mp4
```

* * *

## **MPV Configurations**

MPV ကို စိတ်ကြိုက်ပြုလုပ်ချင်ရင် `mpv.conf` file ကိုသုံးနိုင်ပါတယ်။

### Config File နေရာ

- `~/.config/mpv/mpv.conf`

**ဥပမာ mpv.conf အတွက် Settings:**

```conf
# Default Volume
volume=50

# Enable Hardware Acceleration
hwdec=auto

# Video Scaling Filter
scale=ewa_lanczos

# Subtitle Font Size
sub-font-size=40
```

* * *

## **Keybindings (Shortcut Keys)**

MPV ဟာ အသုံးပြုရအဆင်ပြေအောင် Shortcut Keys တွေကို Default ပါထားပါတယ်။

| Key | Function |
| --- | --- |
| `SPACE` | Play/Pause |
| `q` | Quit MPV |
| `m` | Mute/Unmute Audio |
| `f` | Fullscreen Mode |
| `left/right` | Seek 5 seconds Back/Forward |
| `up/down` | Seek 1 minute Back/Forward |
| `9` and `0` | Decrease/Increase Volume |
| `s` | Take a Screenshot |

* * *

## **MPV Frontends**

GUI အတွက် သုံးချင်ရင် MPV ရဲ့ Frontends တွေ ရှိပါတယ် -

1.  **Celluloid** (GNOME MPV)
2.  **SMPlayer**
3.  **IINA** (macOS အတွက်)

---
### **`mpv` Command Line Options Table**

|Option|Description|Example|
|---|---|---|
|`--no-video`|Video ကိုဖွင့်မနေဘဲ Audio ကိုသာဖွင့်တာ။|`mpv --no-video song.mp3`|
|`--audio-display=no`|Audio ဖွင့်တဲ့အခါ Display မပြတာ။|`mpv --audio-display=no song.mp3`|
|`--loop`|Playlist ကို အဆက်မပြတ် Loop လုပ်ဖို့။|`mpv --loop playlist.m3u`|
|`--volume=50`|အသံအတိုးကို 50% သတ်မှတ်ဖို့။|`mpv --volume=50 music.mp3`|
|`--speed=1.5`|Playback speed ကို 1.5 ဆ ပိုမြန်အောင်လုပ်ရန်။|`mpv --speed=1.5 video.mp4`|
|`--shuffle`|Playlist ထဲက ဖိုင်တွေကို ရွှေ့ပြောင်းဖွင့်ဖို့။|`mpv --shuffle playlist.m3u`|
|`--fullscreen`|Video ကို Fullscreen အတိုင်းဖွင့်ဖို့။|`mpv --fullscreen movie.mp4`|
|`--geometry=50%:50%`|Window position ကို Center မှာထားဖို့။|`mpv --geometry=50%:50% video.mp4`|
|`--autofit=800x600`|Window အရွယ်အစားကို အလိုအလျောက် သတ်မှတ်ရန်။|`mpv --autofit=800x600 video.mp4`|
|`--mute`|အသံကိုတချိန်တည်းအတွင်း Mute လုပ်ဖို့။|`mpv --mute video.mp4`|
|`--sub-file=sub.srt`|Subtitle ဖိုင်ကို ထည့်သွင်းဖို့။|`mpv --sub-file=sub.srt movie.mp4`|
|`--audio-file=audio.mp3`|Video file မပါဘဲ Audio file ကို အသုံးပြုဖို့။|`mpv video.mp4 --audio-file=audio.mp3`|
|`--vo=null`|Video Output ကို ပိတ်ပြီး ဘာမှမပြဖို့။|`mpv --vo=null audio.mp3`|
|`--ytdl`|YouTube-DL ကို အသုံးပြုပြီး Streaming လုပ်ဖို့။|`mpv https://www.youtube.com/watch?v=XXXXX`|
|`--force-window`|Video မရှိတဲ့အခါပဲဖြစ်စေ Window ကို ဖွင့်ထားဖို့။|`mpv --force-window music.mp3`|

---

### 🎵 **အသံနှင့် ပတ်သက်သော Options**

|Option|Description|Example|
|---|---|---|
|`--volume=50`|အသံအတိုးကို 50% သတ်မှတ်ပါ။|`mpv --volume=50 song.mp3`|
|`--mute`|အသံကို Mute လုပ်ပါ။|`mpv --mute song.mp3`|
|`--no-audio`|အသံမဖွင့်ဘဲ Video ကိုသာ ပြပါ။|`mpv --no-audio video.mp4`|
|`--audio-device=DEVICE`|အသံထွက် Device ကိုရွေးပါ။|`mpv --audio-device=alsa`|
|`--audio-channels=stereo`|အသံကို Stereo (၂ဖက်) နဲ့ ထုတ်ပါ။|`mpv --audio-channels=stereo`|

---

### 📺 **ဗီဒီယိုနှင့် ပတ်သက်သော Options**

|Option|Description|Example|
|---|---|---|
|`--no-video`|Video မပါဘဲ အသံသီးသန့် ဖွင့်ပါ။|`mpv --no-video song.mp3`|
|`--audio-display=no`|အသံသီးသန့်ဖြစ်ချိန်မှာ Video မပြပါ။|`mpv --no-video --audio-display=no song.mp3`|
|`--fullscreen`|Video ကို Fullscreen နဲ့ ဖွင့်ပါ။|`mpv --fullscreen movie.mp4`|
|`--geometry=50%:50%`|Video ကို Center မှာ ပြပါ။|`mpv --geometry=50%:50% movie.mp4`|
|`--autofit=800x600`|Video Window အရွယ်အစားကို သတ်မှတ်ပါ။|`mpv --autofit=800x600 movie.mp4`|

---

### 🔁 **ပြန်ဖွင့်ခြင်းနှင့် Loop Options**

|Option|Description|Example|
|---|---|---|
|`--loop`|Playlist ကို အဆုံးမရှိ ပြန်ဖွင့်ပါ။|`mpv --loop playlist.m3u`|
|`--loop-file=3`|တစ်ခုတည်းသော ဖိုင်ကို ၃ ကြိမ် Loop ပြန်ဖွင့်ပါ။|`mpv --loop-file=3 song.mp3`|

---

### 🔀 **အခြား အသုံးဝင်သော Options**

|Option|Description|Example|
|---|---|---|
|`--shuffle`|Playlist ကို Random ဖွင့်ပါ။|`mpv --shuffle playlist.m3u`|
|`--ytdl`|YouTube-DL ကို အသုံးပြုပြီး Video ဖွင့်ပါ။|`mpv --ytdl https://www.youtube.com/watch?v=XXXXX`|
|`--force-window`|Video မပါလည်း Window ဖွင့်ပါ။|`mpv --force-window song.mp3`|
|`--quiet`|Output ကို စကားလုံးနည်းနည်းနဲ့ပြပါ။|`mpv --quiet song.mp3`|
|`--vo=null`|Video Output ကို ပိတ်ပြီး အသံသာထုတ်ပါ။|`mpv --vo=null song.mp3`|

---

### 📝 **လက်တွေ့ အသုံးပြုမှု**

1. **အသံသာ ဖွင့်ပြီး Background မှာ Run လိုတာ**
    
    ```bash
    nohup mpv --no-video --audio-display=no song.mp3 > /dev/null 2>&1 &
    ```
    
2. **YouTube Video ကို Fullscreen နဲ့ ဖွင့်လိုက်တာ**
    
    ```bash
    mpv --fullscreen https://www.youtube.com/watch?v=XXXXX
    ```
    
3. **Playlist ကို Loop လုပ်ပြီး Random ဖွင့်တာ**
    
    ```bash
    mpv --loop --shuffle playlist.m3u
    ```
    

---

