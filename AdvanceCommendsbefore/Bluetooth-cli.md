

### 1. **Bluetooth service ကို စတင်ဖွင့်ပါ**

```bash
sudo systemctl start bluetooth
sudo systemctl enable bluetooth
```

### 2. **Bluetoothctl ကို အသုံးပြုပါ**

`bluetoothctl` ဆိုတာ Bluetooth စီမံခန့်ခွဲမှု tool တစ်ခုပါ။ သူ့အတွက် CLI မှာ အောက်ပါ command ကိုရိုက်ထည့်ပါ။

```bash
bluetoothctl
```

### 3. **Bluetooth ဖွင့်ရန်**

`bluetoothctl` ထဲမှာ `power on` command နဲ့ Bluetooth ကို ဖွင့်ပါ။

```bash
power on
```

### 4. **Bluetooth Device တွေ ရှာဖွေပါ**

Bluetooth device တွေကို ရှာဖွေဖို့ `scan on` ကို အသုံးပြုပါ။

```bash
scan on
```

### 5. **Device ကို ချိပ်ပါ**

ရှာဖွေတဲ့ device တစ်ခုကို ချိပ်ဖို့ `pair` command ကို သုံးပါ။ `XX:XX:XX:XX:XX:XX` သည် device အားလုံးရဲ့ MAC address ဖြစ်ပါသည်။

```bash
pair XX:XX:XX:XX:XX:XX
```

### 6. **Device ကို ချိတ်ဆက်ပါ**

`connect` command ကို အသုံးပြု၍ device ကိုချိတ်ဆက်နိုင်ပါတယ်။

```bash
connect XX:XX:XX:XX:XX:XX
```

### 7. **Device ကို Disconnect ချပါ**

Bluetooth device တစ်ခုကို disconnect ချချင်ရင် `disconnect` command ကို အသုံးပြုပါ။

```bash
disconnect XX:XX:XX:XX:XX:XX
```

### 8. **Bluetoothctl ထဲမှ ထွက်ရန်**

Bluetoothctl tool ထဲမှာ `exit` ကို ရိုက်ပြီး အထွက်နိုင်ပါတယ်။

```bash
exit
```

Bluetooth ကို CLI မှာ ချိပ်နိုင်ပါပြီ။