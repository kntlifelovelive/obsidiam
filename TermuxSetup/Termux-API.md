

---

## 📚 **Termux API Commands Note**

### ✅ `pkg install termux-api`

Termux CLI မှာ API command တွေသုံးဖို့ package ထည့်ဖို့လိုတယ်။

### ✅ [Install Termux:API App (Android side)](https://f-droid.org/en/packages/com.termux.api/)

CLI က Android permission တွေသုံးဖို့ အပေါ်က app ကို install ထည့်ထားဖို့လိုတယ်။

---

## 🔋 Battery

|Command|Usage|
|---|---|
|`termux-battery-status`|Battery percentage, status, temp, current|

📍 Example Output:

```json
{
  "percentage": 88,
  "status": "CHARGING",
  "temperature": 35.2
}
```

---

## 📍 Location (GPS)

|Command|Usage|
|---|---|
|`termux-location`|Get current location (default method=network)|
|`termux-location --provider gps --request once`|One-time GPS location fetch|

📍 Requires location permission allow.

---

## 📷 Camera

|Command|Usage|
|---|---|
|`termux-camera-photo -c 0 -o ~/photo.jpg`|Take photo with back camera|
|`-c 1`|Use front camera|

📍 Requires camera permission.

---

## 🧭 Sensor

|Command|Usage|
|---|---|
|`termux-sensor -l`|List all available sensors|
|`termux-sensor -s accelerometer`|Get live accelerometer data|

---

## 📡 Network & Wi-Fi

|Command|Usage|
|---|---|
|`termux-networkinfo`|Show connection type, IP|
|`termux-wifi-connectioninfo`|Show current Wi-Fi info (SSID, MAC)|
|`termux-wifi-scaninfo`|Scan nearby Wi-Fi networks|
|`termux-telephony-deviceinfo`|SIM & mobile info (carrier, IMEI)|

📍 Requires location permission for Wi-Fi scan.

---

## 📨 SMS & Call

|Command|Usage|
|---|---|
|`termux-sms-send -n 09xxxxxxxx "Hello"`|Send SMS to number|
|`termux-telephony-call 09xxxxxxxx`|Call a number|

📍 Requires phone/SMS permissions

---

## 🔊 Sound & Vibration

|Command|Usage|
|---|---|
|`termux-vibrate -d 500`|Vibrate for 500ms|
|`termux-volume`|Show/change volume levels|

---

## 📋 Clipboard

|Command|Usage|
|---|---|
|`termux-clipboard-get`|Get clipboard content|
|`termux-clipboard-set "Hello"`|Set clipboard content|

---

## 🔔 Notification & Toast

|Command|Usage|
|---|---|
|`termux-notification -t "Title" -c "Message"`|Android notification|
|`termux-toast "Hello!"`|Toast popup at bottom of screen|

---

## 📁 File Sharing

|Command|Usage|
|---|---|
|`termux-share -a send -c "Text to share"`|Share text to Android apps|
|`termux-share -a send -d ~/myfile.txt`|Share file to other apps|

---

## 📂 Storage Access

|Command|Usage|
|---|---|
|`termux-setup-storage`|Allow access to /storage/emulated/0|
|→ Creates `$HOME/storage/shared` symlink||

---

## ⏰ Alarm & Wake Lock

|Command|Usage|
|---|---|
|`termux-wake-lock`|Prevent screen from sleeping|
|`termux-wake-unlock`|Allow sleep again|

---

## 📅 Date & Time

|Command|Usage|
|---|---|
|`termux-dialog date`|Open Android date picker|
|`termux-dialog time`|Open Android time picker|

---

## 🛠 Developer Tools

|Command|Usage|
|---|---|
|`termux-toast "Testing..."`|Show toast message|
|`termux-notification-remove <id>`|Remove specific notification|
|`termux-dialog`|Open input box/dialogs|

---

## 🧪 Custom Example Script

📌 Example: Notify when battery is low

```bash
percent=$(termux-battery-status | jq .percentage)
if [ "$percent" -lt 20 ]; then
  termux-notification -t "Battery Low" -c "$percent% remaining"
fi
```

---

## 🔍 All Termux API Commands List (CLI)

```bash
ls /data/data/com.termux/files/usr/bin/termux-*
```

ဒါနဲ့ မင်းထဲမှာ install လုပ်ထားတဲ့ API command တွေအကုန်ကို မြင်နိုင်တယ်။

---

## 📝 နောက်ထပ် Script Idea?

- 🔋 Battery level alert
- 📸 Motion sensor trigger → take photo
- 🛰 GPS logger script
- 🔒 Vibrate phone when SIM changes (security!)
- 💬 Custom SMS autoresponder

---


**📦 Tip**: `termux-api` နဲ့ combine လုပ်ဖို့ `jq`, `curl`, `bash`, `cron` တို့လည်း ထည့်သင့်တယ်!

---
