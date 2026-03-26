
---


 `adb` နဲ့ `jmtpfs`  *Tools* နှစ်ခုက **phone ကို Linux terminal ကနေ access လုပ်ဖို့သုံးတဲ့ tool** နှစ်မျိုးပါ


|Tool|Purpose|Protocol|
|---|---|---|
|adb|phone control / debugging|ADB protocol|
|jmtpfs|phone storage mount|MTP|


---

# 1 ADB (Android Debug Bridge)

ADB က **Android device control tool** ဖြစ်ပါတယ်။

Google developer tools ထဲကတစ်ခုပါ။

ADB နဲ့လုပ်လို့ရတာတွေ 

- phone shell access
    
- file transfer
    
- install apk
    
- log viewing
    
- debugging
    
- screen record
    
- port forwarding
    


---

## ADB install

Arch / Arch-based

```bash
sudo pacman -S android-tools
```

Debian / Kali / Ubuntu

```bash
sudo apt install adb
```

check

```bash
adb version
```

---

# 2 Phone setup

phone မှာ

```
Developer Options
 → USB debugging ON
```

USB cable နဲ့ connect လုပ်ပါ။

---

# 3 device detect

```bash
adb devices
```

example

```
List of devices attached
R58N123ABC device
```

 phone မှာ **Allow USB debugging** popup လာရင် Allow နှိပ်ရပါတယ်။

---

# 4 phone shell access

```bash
adb shell
```

output

```
generic_x86:/ $
```

ဒါဆို **phone Linux shell** ထဲဝင်သွားပြီ။

example commands

```bash
ls /sdcard
```

```bash
df -h
```

---

# 5 file copy (phone → pc)

```bash
adb pull /sdcard/DCIM/photo.jpg
```

---

# 6 file copy (pc → phone)

```bash
adb push file.txt /sdcard/Download/
```

---

# 7 install apk

```bash
adb install app.apk
```

---

# 8 screen record

```bash
adb shell screenrecord /sdcard/video.mp4
```

stop → Ctrl+C

download

```bash
adb pull /sdcard/video.mp4
```

---

# 9 phone reboot

```bash
adb reboot
```

bootloader

```bash
adb reboot bootloader
```

---

# 10 phone apps list

```bash
adb shell pm list packages
```

system apps

```bash
adb shell pm list packages -s
```

---

---

---

# 2 jmtpfs (MTP filesystem)

`jmtpfs` က

**Android phone storage ကို Linux folder တစ်ခုလို mount လုပ်ပေးတဲ့ tool** ဖြစ်ပါတယ်။

protocol

```
MTP (Media Transfer Protocol)
```

---

## install

Arch

```bash
sudo pacman -S jmtpfs
```

Debian / Kali

```bash
sudo apt install jmtpfs
```

---

# mount phone storage

phone

```
USB mode → File Transfer
```

ပြီးရင်

```bash
mkdir ~/phone
jmtpfs ~/phone
```

---

# storage list

```bash
ls ~/phone
```

example

```
DCIM
Download
Movies
Music
Pictures
```

ဒါဆို phone storage ကို **Linux folder လိုသုံးလို့ရပြီ**။

---

# copy files

example

```bash
cp video.mp4 ~/phone/Movies
```

---

# unmount

```bash
fusermount -u ~/phone
```

---

# adb vs jmtpfs

|feature|adb|jmtpfs|
|---|---|---|
|phone control|✔|✖|
|shell access|✔|✖|
|file transfer|✔|✔|
|debugging|✔|✖|
|storage mount|✖|✔|
|root access|possible|✖|

---
