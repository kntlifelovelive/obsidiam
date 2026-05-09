

- ip show 

```shell

nmcli connection show 

```




- create 

```shell 

# bridge interface အသစ်ဖန်တီးပါ
sudo nmcli connection add type bridge ifname br0 con-name bridge-br0

# STP ပိတ်ပါ
sudo nmcli connection modify bridge-br0 bridge.stp no

# enp1s0 ကို bridge ထဲထည့်ပါ
sudo nmcli connection add type ethernet slave-type bridge con-name bridge-br0-slave ifname enp1s0 master bridge-br0

# enp1s0 ရဲ့ original connection ကို disable လုပ်ပါ (အရင်ဆုံး connection name သိရန်)
sudo nmcli connection down "Wired connection 1"   # ဒီနေရာမှာ အဆင့် ၁ မှာရခဲ့တဲ့ name ထည့်ပါ

# bridge ကို activate လုပ်ပါ
sudo nmcli connection up bridge-br0

```





အင်း ခင်ဗျားရဲ့ current connections တွေကို မြင်ရပါတယ်။ အခု bridge interface ဖန်တီးတဲ့အဆင့်တွေကို **အသေးစိတ်** ပြန်ပြောပြပါမယ်။

## လက်ရှိ Connections အခြေအနေ

```
Wired connection 1    (enp1s0) - Ethernet connection (IP: 192.168.99.60)
U Thar Thana          (wlan0)   - WiFi connection (IP: 192.168.100.209)
```

## Bridge Interface ဖန်တီးခြင်း (အသေးစိတ်)

### အဆင့် ၁။ Bridge Interface အသစ် Create လုပ်ခြင်း

```bash
sudo nmcli connection add type bridge ifname br0 con-name bridge-br0
```

**ဘာလုပ်လဲ**: `br0` ဆိုတဲ့ bridge interface အသစ်ကို ဖန်တီးပါတယ်။
- `type bridge` - bridge အမျိုးအစား
- `ifname br0` - interface name ကို br0 လို့သတ်မှတ်
- `con-name bridge-br0` - connection name ကို bridge-br0 လို့သတ်မှတ်

**ရလဒ်**: Connection name `bridge-br0` နဲ့ interface `br0` ပေါ်လာမယ်။

---

### အဆင့် ၂။ STP (Spanning Tree Protocol) ပိတ်ခြင်း

```bash
sudo nmcli connection modify bridge-br0 bridge.stp no
```

**ဘာလုပ်လဲ**: STP ကို ပိတ်ပါတယ်။ ဒါက network performance ကို မြန်စေပြီး simple home network အတွက် မလိုအပ်ပါဘူး။

---

### အဆင့် ၃။ enp1s0 ကို Bridge ထဲထည့်ခြင်း

```bash
sudo nmcli connection add type ethernet slave-type bridge con-name bridge-br0-slave ifname enp1s0 master bridge-br0
```

**ဘာလုပ်လဲ**: `enp1s0` interface ကို `bridge-br0` ရဲ့ slave (အဖွဲ့ဝင်) အဖြစ်ထည့်ပါတယ်။
- `type ethernet` - ethernet အမျိုးအစား
- `slave-type bridge` - bridge ရဲ့ slave ဖြစ်မယ်
- `con-name bridge-br0-slave` - slave connection name
- `ifname enp1s0` - enp1s0 interface ကိုသုံးမယ်
- `master bridge-br0` - master က bridge-br0 ဖြစ်မယ်

**ရလဒ်**: `bridge-br0-slave` ဆိုတဲ့ connection အသစ်ပေါ်လာမယ်။

---

### အဆင့် ၄။ Original Wired Connection ကို Disable လုပ်ခြင်း

```bash
sudo nmcli connection down "Wired connection 1"
```

**ဘာလုပ်လဲ**: လက်ရှိသုံးနေတဲ့ `Wired connection 1` ကို ပိတ်ပါတယ်။ ဒီအချိန်မှာ **SSH connection ပြတ်သွားနိုင်တယ်** (192.168.99.60 နဲ့ချိတ်ထားရင်)။

**သတိချပ်စရာ**: 
- SSH နဲ့ချိတ်ထားရင် ဒီ command ရိုက်ပြီးချင်း connection ပြတ်သွားပါမယ်။
- ဒါကြောင့် **ဒီ command ကို နောက်ဆုံးမှ ရိုက်ပါ** (သို့) **WiFi IP (192.168.100.209) နဲ့ အရင်ချိတ်ထားပါ**။

---

### အဆင့် ၅။ Bridge ကို Activate လုပ်ခြင်း

```bash
sudo nmcli connection up bridge-br0
```

**ဘာလုပ်လဲ**: အသစ်ဖန်တီးထားတဲ့ `bridge-br0` connection ကို စတင်အသုံးပြုပါတယ်။

**ဖြစ်လာမယ့်အခြေအနေ**:
- bridge interface `br0` က active ဖြစ်လာမယ်
- `enp1s0` က bridge ရဲ့ slave အဖြစ် အလုပ်လုပ်မယ်
- IP address က `br0` မှာ ပေါ်လာမယ် (DHCP က အလုပ်လုပ်ရင်)

---

## အဆင့်တွေကို တစ်စုတစ်စည်းတည်း ပြန်လုပ်နည်း

### နည်းလမ်း ၁ - တစ်ခုချင်းစီ ရိုက်နည်း

```bash
# 1. Bridge interface ဖန်တီးပါ
sudo nmcli connection add type bridge ifname br0 con-name bridge-br0

# 2. STP ပိတ်ပါ
sudo nmcli connection modify bridge-br0 bridge.stp no

# 3. enp1s0 ကို bridge ထဲထည့်ပါ
sudo nmcli connection add type ethernet slave-type bridge con-name bridge-br0-slave ifname enp1s0 master bridge-br0

# 4. Original connection ကို disable လုပ်ပါ (SSH ပြတ်မယ်)
sudo nmcli connection down "Wired connection 1"

# 5. Bridge ကို activate လုပ်ပါ
sudo nmcli connection up bridge-br0
```

### နည်းလမ်း ၂ - Script တစ်ခုအနေနဲ့ သိမ်းပြီး run နည်း

```bash
# script file ဖန်တီးပါ
cat > ~/setup-bridge.sh << 'EOF'
#!/bin/bash
echo "Creating bridge interface..."
sudo nmcli connection add type bridge ifname br0 con-name bridge-br0

echo "Disabling STP..."
sudo nmcli connection modify bridge-br0 bridge.stp no

echo "Adding enp1s0 to bridge..."
sudo nmcli connection add type ethernet slave-type bridge con-name bridge-br0-slave ifname enp1s0 master bridge-br0

echo "Disabling original wired connection..."
sudo nmcli connection down "Wired connection 1"

echo "Activating bridge..."
sudo nmcli connection up bridge-br0

echo "Bridge setup complete!"
EOF

# script ကို executable လုပ်ပါ
chmod +x ~/setup-bridge.sh

# script ကို run ပါ
~/setup-bridge.sh
```

---

## Bridge ပြီးရင် စစ်ဆေးရမယ့်အဆင့်များ

### ၁။ Bridge interface ကို စစ်ဆေးပါ

```bash
# bridge interface ရှိလား စစ်ပါ
ip link show type bridge

# ရလဒ်: br0 ဆိုတာ ပေါ်ရမယ်
```

### ၂။ IP address ရလား စစ်ပါ

```bash
ip addr show br0
```

**IP မရရင်** - DHCP ကို ပြန် run ပါ။

```bash
# DHCP ပြန်ရှာဖို့
sudo dhclient br0

# ဒါမှမဟုတ် NetworkManager ကို restart လုပ်ပါ
sudo nmcli connection down bridge-br0
sudo nmcli connection up bridge-br0
```

### ၃။ IP မရသေးရင် manual IP ထည့်ပါ

```bash
# manual IP ထည့်ခြင်း
sudo nmcli connection modify bridge-br0 ipv4.addresses 192.168.99.60/24
sudo nmcli connection modify bridge-br0 ipv4.gateway 192.168.99.1
sudo nmcli connection modify bridge-br0 ipv4.dns "8.8.8.8 8.8.4.4"
sudo nmcli connection modify bridge-br0 ipv4.method manual

# bridge ကို restart လုပ်ပါ
sudo nmcli connection down bridge-br0
sudo nmcli connection up bridge-br0
```

### ၄။ Connection list ကို စစ်ဆေးပါ

```bash
nmcli connection show
```

ဒီမှာ အောက်ပါအတိုင်း ပေါ်ရမယ်:
```
NAME                UUID                                  TYPE      DEVICE
bridge-br0          xxx-xxx-xxx                           bridge    br0
bridge-br0-slave    xxx-xxx-xxx                           ethernet  enp1s0
U Thar Thana        xxx-xxx-xxx                           wifi      wlan0
Wired connection 1  xxx-xxx-xxx                           ethernet  --    (inactive)
```

---

## အရေးကြီးသတိပေးချက်

### SSH Connection ပြတ်သွားရင် ဘယ်လိုပြန်ချိတ်မလဲ

1. **WiFi IP နဲ့ ပြန်ချိတ်ပါ**:
   ```bash
   ssh user@192.168.100.209
   ```

2. **ဒါမှမဟုတ်** physical terminal (monitor + keyboard) နဲ့ ဝင်ပါ

3. **ပြီးရင်** bridge setup ကို ဆက်လုပ်ပါ

### မအောင်မြင်ရင် ပြန်ဖျက်မယ့်နည်း

```bash
# bridge ကို ဖယ်ရှားပါ
sudo nmcli connection down bridge-br0
sudo nmcli connection delete bridge-br0
sudo nmcli connection delete bridge-br0-slave

# Wired connection 1 ကို ပြန် activate လုပ်ပါ
sudo nmcli connection up "Wired connection 1"

# IP ပြန်ရလား စစ်ပါ
ip addr show enp1s0
```

---

## Troubleshooting Tips

### 1. Bridge မှာ IP မရရင်
```bash
# NetworkManager state စစ်ပါ
nmcli device status

# bridge-br0 configuration စစ်ပါ
nmcli connection show bridge-br0 | grep ipv4
```

### 2. enp1s0 က bridge ထဲမှာ မပါရင်
```bash
# bridge ports စစ်ပါ
brctl show br0

# enp1s0 ကို manual ထပ်ထည့်ပါ
sudo ip link set enp1s0 master br0
```

### 3. Internet မရရင်
```bash
# ping test
ping -c 4 8.8.8.8
ping -c 4 google.com

# DNS စစ်ပါ
cat /etc/resolv.conf
```

ဒီအဆင့်တွေ လုပ်ပြီးရင် ဘယ်နေရာမှာ ပြဿနာရှိလဲဆိုတာ ပြန်ပြီး ပြောပြပါ။ ဆက်လက်ကူညီပေးပါ့မယ်။