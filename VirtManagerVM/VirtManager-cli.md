

---

# KVM/QEMU VM Command Line(Full Setup)

## 1. ပုံသေ Session သတ်မှတ်ခြင်း (တစ်ကြိမ်သာ လုပ်ရန်)

- VM တွေကို `sudo` မပါပဲ စီမံနိုင်ဖို့ အောက်ပါအတိုင်း ပြုလုပ်ပါ။

```bash
# ပုံသေ URI ကို system session အဖြစ် သတ်မှတ်ပါ
echo 'export LIBVIRT_DEFAULT_URI=qemu:///system' >> ~/.zshrc 

# လက်ရှိ terminal မှာ ချက်ချင်းသက်ဝင်စေရန်
source ~/.zshrc

# အတည်ပြုစစ်ဆေးပါ
virsh uri
# Output: qemu:///system ဆိုပြီး ပြရပါမယ်
```

---

## 2. VM ကို Command Line ကနေ စတင်ခြင်း

```bash
# VM အားလုံးကို ကြည့်ရန်
virsh list --all

# VM စတင်ရန်
virsh start <vm-name>

# ဥပမာ
virsh start archlinux
virsh start ubuntu24.04

# VM အခြေအနေ စစ်ဆေးရန်
virsh list
```

---

## 3. VM ၏ IP Address ရှာဖွေခြင်း

```bash
# VM ရဲ့ IP ကို တိုက်ရိုက်ရှာရန်
virsh domifaddr <vm-name>

# ဥပမာ
virsh domifaddr archlinux

# အထွက်ပုံစံ
# Name       MAC address          Protocol     Address
# ----------------------------------------------------------------------------
# vnet0      52:54:00:xx:xx:xx    ipv4         192.168.122.100/24
```

---

## 4. SSH (Connect) ဖြင့် ချိတ်ဆက်ခြင်း 

```bash
# VM ထဲကို SSH ဝင်ရန်
ssh <username>@<vm-ip>

# ဥပမာ
ssh arch@192.168.122.100
ssh archibuti@192.168.122.213 # ယခု လက်ရှိ ubuntu24.04 server တင်ထားသည်။ 
```

#### .SSH Key သတ်မှတ်ခြင်း (Password မလို)

```bash
# SSH key ဖန်တီးရန် (မရှိသေးရင်)
ssh-keygen -t ed25519

# Key ကို VM ထဲကို ကူးထည့်ရန်
ssh-copy-id <username>@<vm-ip>

# ဥပမာ
ssh-copy-id arch@192.168.122.100
```

---

## 5. VM ကို ပိတ်ခြင်း

```bash
# VM ကို ချောမွေ့စွာပိတ်ရန်
virsh shutdown <vm-name>

# အတင်းပိတ်ရန် (အရေးပေါ်ကိစ္စမှသာ)
virsh destroy <vm-name>
```

---

## 6. VM အလိုအလျောက် စတင်ခြင်း (Auto-start)

Host စက်နဲ့အတူ VM ကို အလိုအလျောက် စတင်ချင်ရင်

```bash
# Auto-start ဖွင့်ရန်
virsh autostart <vm-name>

# Auto-start ပိတ်ရန်
virsh autostart --disable <vm-name>

# စစ်ဆေးရန်
virsh list --all --autostart
```

---

## 7. Essential Commands

| Command | ရှင်းလင်းချက် |
|---------|---------------|
| `virsh list --all` | VM အားလုံးကို ပြရန် |
| `virsh start <name>` | VM စတင်ရန် |
| `virsh shutdown <name>` | VM ပိတ်ရန် |
| `virsh reboot <name>` | VM ပြန်စတင်ရန် |
| `virsh domifaddr <name>` | VM ၏ IP ပြရန် |
| `virsh console <name>` | VM console ထဲဝင်ရန် (Ctrl + ] နဲ့ထွက်) |
| `virsh autostart <name>` | Host နဲ့အတူ auto-start ဖွင့်ရန် |
| `virsh uri` | လက်ရှိ session path ပြရန် |

---

## 8. အလုပ်လုပ်ပုံ အဆင့်ဆင့် (Workflow)

```bash
# 1. VM ကို စတင်ပါ
virsh start archlinux

# 2. IP ရှာပါ
virsh domifaddr archlinux

# 3. SSH ဝင်ပါ
ssh arch@192.168.122.100

# 4. VM ထဲမှာ အလုပ်လုပ်ပါ
#    (commands, services, etc.)

# 5. ပြီးရင် SSH ကနေ ထွက်ပါ
exit

# 6. VM ကို ပိတ်ပါ
virsh shutdown archlinux
```

---

## 9. Note

1. **ပုံသေ URI** ကို `.bashrc` မှာ ထည့်ထားလိုက်ရင် terminal အသစ်ဖွင့်တိုင်း `qemu:///system` ကို auto ချိတ်ပေးပါလိမ့်မယ်။

2. **Virt-manager** နဲ့ `virsh` က တူညီတဲ့ VM တွေကို စီမံပါတယ်။ တစ်ခုခုနဲ့ ပြောင်းလဲလိုက်ရင် နောက်တစ်ခုမှာလည်း အလိုအလျောက် ပြောင်းသွားပါလိမ့်မယ်။

3. **SSH မဝင်ရသေးရင်** - VM ထဲမှာ `openssh-server` ကို install လုပ်ထားဖို့ လိုပါတယ်။
   ```bash
   # VM ထဲမှာ (ubuntu/debian)
   sudo apt install openssh-server -y

   # VM ထဲမှာ (arch)
   sudo pacman -S openssh
   sudo systemctl enable --now sshd
   ```

---

