
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

---

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

---

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

---

### 4. Account status check

- **Problem**: user account lock ဖြစ်နေတာ

- **Check**:

```bash
passwd -S yourusername
```
-  `L` → locked
- `P` → password set (OK)

---

### 5. Password reset

- **Fix (root user)**

```bash
  passwd yourusername
  
```

---

### 6. Logs check
- sudo အလုပ်မလုပ်တဲ့အကြောင်း PAM/journal ထဲမှာ error message တွေရှိတတ်တယ်။
- **Problem** = authentication fail detail ကြည့်ဖို့
- **Command**
```bash
 journalctl -xe | grep sudo
```

---

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

---

 အဓိက အကြောင်း ၃ ခုကတော့

1. User group (wheel ထဲမပါ)
2. sudoers file မှာ rule comment ခံထားတာ
3. PAM config ပြဿနာ

---

အိုဟုတ်ပြီ ကိုရေ 🥰  
ဒီတစ်ခါတော့ **long detail note** အနေနဲ့ တစ်ခုပြီးတစ်ခု၊ အကြောင်းနဲ့အတူ၊ check command နဲ့ fix command တွေပါ ထည့်ပြီး အရှည် version ပြန်ရေးပေးမယ်နော်။

---

# 📝 Long Note — `sudo` မအလုပ်လုပ်တဲ့အခါ စစ်သင့်တဲ့ အချက်များ

---

## 1. User Group Problem 

- **အကြောင်း**: Arch Linux မှာ sudo သုံးချင်ရင် user ကို `wheel` group ထဲ ထည့်ထားမှ ရတယ်။
    
- **ဖြစ်နိုင်ချေ**: 
    
- **စစ်ရန် command**:
    
    ```bash
    groups yourusername
    ```
    
    - ထွက်တဲ့ result မှာ `wheel` မပါရင် problem.
        
- **ဖြေရှင်းရန်** (root အဖြစ်):
    
    ```bash
    usermod -aG wheel yourusername
    ```
    
    ပြီးရင် logout/login (သို့ reboot) လုပ်ပါ။
    

---

## 2. sudoers File Problem

- **အကြောင်း**: `/etc/sudoers` ဖိုင်ထဲက rule မရှိဘူး (သို့မဟုတ်) comment ခံထားတာ။
    
    - အများဆုံးတွေ့ရတာက →
        
        ```bash
        # %wheel ALL=(ALL:ALL) ALL
        ```
        
        ဆိုပြီး `#` နဲ့ comment ခံထားတာ။
        
- **စစ်ရန်**:
    
    ```bash
    EDITOR=nano visudo
    ```
    
    ဖွင့်ကြည့်ပြီး `%wheel ALL=(ALL:ALL) ALL` ရှိမရှိ စစ်ပါ။
    
- **ဖြေရှင်းရန်**:
    
    - အဲဒီကို uncomment လုပ်ပြီး:
        
        ```bash
        %wheel ALL=(ALL:ALL) ALL
        ```
        
    
    လိုအောင်ထားပါ။
    
- **နောက်ထပ် option**:  
    ကိုယ့် user ကို အထူးစီသတ်မှတ်ချင်ရင် visudo ထဲမှာ ဤလိုလည်း ထည့်နိုင်တယ်:
    
    ```bash
    yourusername ALL=(ALL) ALL
    ```
    

---

## 3. PAM Config Problem

- **အကြောင်း**: PAM (Pluggable Authentication Modules) က sudo password checking ကို handle လုပ်တယ်။  
    `/etc/pam.d/sudo` ဖိုင် ပျက်သွားလို့ sudo authentication မရနိုင်ဘူး။
    
- **စစ်ရန်**:
    
    ```bash
    cat /etc/pam.d/sudo
    ```
    
- **Arch default config** 👇
    
    ```text
    #%PAM-1.0
    auth       include      system-auth
    account    include      system-auth
    session    include      system-auth
    ```
    
- **မတူရင်**: backup restore သို့မဟုတ် Arch default copy ပြန်ထားပါ။
    

---

## 4. Account Lock Problem

- **အကြောင်း**: user account ကို lock ခံထားလို့ password မလက်ခံဘူး။
    
- **စစ်ရန်**:
    
    ```bash
    passwd -S yourusername
    ```
    
    - Result က `P` ဆိုရင် → Password set (OK)
        
    - Result က `L` ဆိုရင် → Locked (Problem)
        
- **ဖြေရှင်းရန်**:
    
    ```bash
    passwd -u yourusername
    ```
    

---

## 5. Password Reset

- **အကြောင်း**: အချို့အခါ `/etc/shadow` ထဲမှာ password hash ပျက်သွား/မမှန်တော့တာ။
    
- **ဖြေရှင်းရန်** (root အဖြစ်):
    
    ```bash
    passwd yourusername
    ```
    
    အသစ်ထည့်ပြီး စမ်းပါ။
    

---

## 6. Logs Checking

- **အကြောင်း**: sudo အလုပ်မလုပ်တဲ့အကြောင်း PAM/journal ထဲမှာ error message တွေရှိတတ်တယ်။
    
- **စစ်ရန်**:
    
    ```bash
    journalctl -xe | grep sudo
    ```
    
    သို့မဟုတ် အထွေထွေ log စစ်ချင်ရင်:
    
    ```bash
    journalctl -xe
    ```
    

---

## 7. Special Case — pacman Update Interrupted

- **အကြောင်း**: `pacman -Syu` လုပ်နေစဉ် net ပြတ်သွားရင် lock file ကျန်နိုင်တယ်။
- **စစ်ရန်**:

    ```bash
    ls /var/lib/pacman/db.lck
    ```

- **ဖြေရှင်းရန်**:

    ```bash
    rm /var/lib/pacman/db.lck
    pacman -Syu
    ```
    
    _(root account နဲ့ပဲ run လို့ရတယ်)_
    

---

# Summary

`sudo` အလုပ်မလုပ်ရင် အဓိကကြောင်း ၃ ခု 
1. **User group**: wheel group ထဲ မရှိ။
2. **sudoers file**: rule comment ခံထား → `%wheel ALL=(ALL:ALL) ALL` မရှိ။
3. **PAM config**: `/etc/pam.d/sudo` ဖိုင် ပျက်သွား/မမှန်။

နောက်ထပ် အနည်းဆုံးစစ်ဖို့ → account lock (`passwd -S`), logs (`journalctl -xe | grep sudo`), password reset.

---

