
---

## Note — `sudo` အလုပ်မလုပ်တဲ့အခါ စစ်ရမည်အချက်များ

### 1. User group check (wheel group)

- **Problem**: user က `wheel` group ထဲ မရှိလို့ sudo အသုံးပြုခွင့်မရ။
- **Check Command**

```bash
 groups yourusername
 
```

- **Fix Command**

```bash
   usermod -aG wheel yourusername
```


### 2. sudoers file check

- **Problem**: `/etc/sudoers` မှာ `%wheel ALL=(ALL:ALL) ALL` ကို comment ခံထားတယ် (# လို)
- **Check/Edit**:

```bash 
EDITOR=nano visudo

```

- **Fix**: ဒီလို uncomment လုပ်ပါ 

```bash

%wheel ALL=(ALL:ALL) ALL

```


### 3. PAM config check

- **Problem**: `/etc/pam.d/sudo` ဖိုင် ပျက်သွား သို့မဟုတ် misconfig ဖြစ်တယ်
- **Check**
```bash
cat /etc/pam.d/sudo
```

- **Default content** (Arch) 

```text

    #%PAM-1.0
    auth       include      system-auth
    account    include      system-auth
    session    include      system-auth
    
```


### 4. Account status check

- **Problem**: user account lock ဖြစ်နေတာ

- **Check**:

```bash
passwd -S yourusername
```
-  `L` → locked
- `P` → password set (OK)

### 5. Password reset

- **Fix (root user)**

```bash
  passwd yourusername
  
```


### 6. Logs check
- sudo အလုပ်မလုပ်တဲ့အကြောင်း PAM/journal ထဲမှာ error message တွေရှိတတ်တယ်။
- **Problem** = authentication fail detail ကြည့်ဖို့
- **Command**
```bash
 journalctl -xe | grep sudo
```


#  Special Case (Update Interrupted)

- **Symptom**: `pacman -Syu` net ပြတ်ပြီး အလယ်မှာရပ်သွား
- **Check**
```bash
ls /var/lib/pacman/db.lck
```
- *Fix*
```bash
rm /var/lib/pacmandb.lck
pacman -Syu

```


1. User group (wheel ထဲမပါ)
2. sudoers file မှာ rule comment ခံထားတာ
3. PAM config ပြဿနာ

###  Long Note — `sudo` မအလုပ်လုပ်တဲ့အခါ စစ်သင့်တဲ့ အချက်များ

## 1. User Group Problem 

```bash 
groups yourusername
```
- ==> result မှာ `wheel` မပါရင် problem
- ==> (root change)

```bash
 usermod -aG wheel yourusername

```
- ပြီးရင် logout/login (သို့ reboot) လုပ်ပါ။

## 2. sudoers File Problem

- **အကြောင်း**: `/etc/sudoers` ဖိုင်ထဲက rule မရှိဘူး (သို့မဟုတ်) comment ခံထားတာ။ 
- အများဆုံးတွေ့ရတာက 

```bash
# %wheel ALL=(ALL:ALL) ALL
```
