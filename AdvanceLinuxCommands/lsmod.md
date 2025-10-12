
---

##### *Run `lsmod` at the command line to find out what kernel modules are currently loaded*

```bash

lsmod 

```

---
## 🔹 `lsmod` (list modules)

**ဘာလုပ်သလဲ?**
- Kernel မှာ လက်ရှိ load လုပ်ထားတဲ့ module (drivers) တွေကို စာရင်းထုတ်ပြပေးတယ်။
- RAM ထဲမှာ load ဖြစ်နေတဲ့ kernel driver တွေကိုကြည့်ချင်ရင် သုံးတယ်။

**ဘယ်နေရာမှာ သုံးလဲ?**
- USB device တစ်ခုထည့်လိုက်ပြီး driver load ဖြစ်သလား စစ်ချင်တဲ့အခါ
- Network card, sound card driver လိုအပ်တဲ့ device တွေကို check လုပ်ချင်တဲ့အခါ
- Kernel module troubleshooting လုပ်တဲ့အခါ

**Example**

```bash
lsmod
```

Output 

```
Module                  Size  Used by
nvidia              12345678  50
snd_hda_intel        57344    3
iwlwifi              348160   0
```

==> `Module` = module name  
==> `Size` = memory usage  
==> `Used by` = အခြား module များ ဘယ်နှစ်ခုက ဒီ module ကိုသုံးနေလဲ

---

## 🔹 `modinfo` (module information)

**ဘာလုပ်သလဲ?**
- Module file (.ko) အကြောင်းအသေးစိတ်ကို ပြပေးတယ်။
- Version, author, license, description, supported parameters တို့ကြည့်နိုင်တယ်။

**ဘယ်နေရာမှာ သုံးလဲ?**
- အဲ့ဒီ module ရဲ့ author, version, description ကိုကြည့်ချင်တဲ့အခါ
- အဲ့ဒီ module သုံးတဲ့ parameters (option flags) ကိုကြည့်ချင်တဲ့အခါ
- Kernel debugging / module customization လိုအပ်တဲ့အခါ

**Example**

```bash
modinfo iwlwifi
```

Output 

```
filename:       /lib/modules/6.6.5-arch1-1/kernel/drivers/net/wireless/intel/iwlwifi.ko.zst
license:        GPL
author:         Intel Corporation
description:    Intel(R) Wireless WiFi driver for Linux
version:        6.6.5
parm:           power_save:int
```

==> `filename` = module file path  
==> `license` = GPL (free software)  
==> `parm` = ဒီ module ကို load လုပ်တဲ့အခါ သုံးနိုင်တဲ့ parameter

---


###  quick overview

- `lsmod` → list currently loaded kernel modules (who's loaded now). ([man7.org](https://man7.org/linux/man-pages/man8/lsmod.8.html?utm_source=chatgpt.com "lsmod(8) - Linux manual page"))
- `modinfo` → get detailed info about a module file (params, author, license, filename). ([man7.org](https://man7.org/linux/man-pages/man8/modinfo.8.html?utm_source=chatgpt.com "modinfo(8) - Linux manual page"))

---

## 1. Hardware detect / driver in-use စစ်ပါ။

- Check kernel logs first

 ```bash
    sudo dmesg --ctime | tail -n 50
    # or use journalctl for systemd systems
    sudo journalctl -k -n 200
```



## 2.module load ဖြစ်/မဖြစ် `lsmod` နဲ့ စစ်ပါ။

- Simple list:

 ```bash
 
  lsmod
  

  ```
  
- Filter by name (example WiFi / sound)

```bash
	lsmod | grep -i iwlwifi
    lsmod | grep -i snd
```


## 3. ဒီ module ရဲ့ အသေးစိတ်ကို `modinfo` နဲ့ကြည့်ပါ။

- Basic:

    ```bash
    modinfo iwlwifi
    ```

- Only specific field (e.g., filename or version)

    ```bash
    modinfo -F filename iwlwifi
    modinfo -F version iwlwifi
    ```

 

## 4. Module parameter values  runtime  `/sys/module` chack

- Example:

    ```bash
    ls /sys/module/iwlwifi/parameters
    cat /sys/module/iwlwifi/parameters/power_save
    ```


## 5. Module (re)load / unload — test with options

- Unload (if safe — beware dependencies):
    
    ```bash
    sudo modprobe -r iwlwifi    # safer: modprobe -r removes with dep handling
    # or force (risky)
    sudo rmmod iwlwifi
    ```


- Load with parameter:
- 
    ```bash
    sudo modprobe iwlwifi power_save=0
    ```
    
    → `modprobe` က dependency handling ပေးတယ်၊ `insmod` က raw insert (path/file) သာ။ ([Oracle Docs](https://docs.oracle.com/en/operating-systems/oracle-linux/6/admin/ol_modparams.html?utm_source=chatgpt.com "5.4 About Module Parameters"))
    


## 6. Permanent option (boot-time) `/etc/modprobe.d/` config 

- Example to disable power save permanently:
    
    ```bash
    echo "options iwlwifi power_save=0" | sudo tee /etc/modprobe.d/iwlwifi.conf
    sudo update-initramfs -u   # Debian/Ubuntu only; or rebuild initramfs for your distro
    ```

## 7.Driver not present or wrong driver in-use → check which driver bound to device

- For PCI devices:
    
    ```bash
    lspci -k    # shows kernel driver in use / available
    ```
    
- For USB devices:
    
    ```bash
    lsusb
    # find bus id then:
    sudo dmesg | grep -i usb
    ```
    
    → `lspci -k` useful to see which kernel module currently handles that device. ([Engineering LibreTexts](https://eng.libretexts.org/Bookshelves/Computer_Science/Operating_Systems/Linux_-_The_Penguin_Marches_On_%28McClanahan%29/06%3A_Kernel_Module_Management/2.05%3A_Kernel_Module_Management_-_lsmod_Command?utm_source=chatgpt.com "Kernel Module Management - lsmod/modinfo Command"))
    

## 8. If module missing on disk (module file not found)

- `modinfo` will try to find file in `/lib/modules/$(uname -r)/...`. If not found, you may need matching kernel headers or install driver package. Use:
    
    ```bash
    modinfo <modulename>
    ```
    
    If it errors, check `/lib/modules/$(uname -r)` and run:
    
    ```bash
    sudo depmod -a
    sudo modprobe <module>
    ```
    
    → often kernel version mismatch causes module-not-found. ([linux.die.net](https://linux.die.net/man/8/modinfo?utm_source=chatgpt.com "modinfo(8): show info about Kernel module - Linux man page"))
    

## 9. Advanced tools to inspect module params & state

- `systool` (from `sysfsutils`) — shows module parameters nicely:
    
    ```bash
    sudo apt install sysfsutils   # or distro equivalent
    sudo systool -vm iwlwifi
    ```

→ shows Parameters section. ([Server Fault](https://serverfault.com/questions/62316/how-do-i-list-loaded-linux-module-parameter-values?utm_source=chatgpt.com "How do I list loaded Linux module parameter values?"))


---

# Useful example: WiFi not working — concise checklist

1. `sudo dmesg --ctime | grep -i iwlwifi` → see errors.
2. `lsmod | grep iwlwifi` → module loaded?
3. `modinfo iwlwifi` → supported params, firmware filename.
4. `ls /lib/firmware | grep iwl` → firmware present? (driver often needs firmware blob)
5. `sudo modprobe -r iwlwifi && sudo modprobe iwlwifi` → reload driver.
6. `sudo journalctl -k -f` while plugging the device → live logs. ([linuxjournal.com](https://www.linuxjournal.com/content/leveraging-modprobe-and-lsmod-effective-linux-system-management?utm_source=chatgpt.com "Leveraging modprobe and lsmod for Effective Linux ..."))

---

# Quick cheatsheet (commands)

```
lsmod                          # list loaded modules
lsmod | grep <name>            # filter
modinfo <module>               # full info
modinfo -F filename <module>   # show specific field
cat /sys/module/<mod>/parameters/<parm>  # runtime param value
modprobe <module>              # load (with deps)
modprobe -r <module>           # remove (with deps)
rmmod <module>                 # remove (force, risky)
systool -vm <module>           # show Params (if installed)
lspci -k                       # see driver bound to PCI device
dmesg / journalctl -k          # kernel logs
```
