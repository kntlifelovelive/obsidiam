
---

#  USB / SSD Format Note

##  Device name စစ်ပါ (Important)

```bash
lsblk
```

- `/dev/sda` = system disk (မထိပါနဲ့ ❗)
    
- `/dev/sdb`, `/dev/sdc` = USB / External
    

---

## MBR (msdos) Partition Table လုပ်နည်း

```bash
sudo fdisk /dev/sdc or sdc1  == lsblk device name ထည့်ရန် 
```

Inside fdisk:

```
o   → new MBR table
n   → new partition
Enter Enter Enter
w   → write & exit
```

---

##  exFAT Format (Android + Linux Best)

exfat tools မရှိရင် install:

### Arch / Manjaro

```bash
sudo pacman -S exfatprogs
```

### Debian / Ubuntu

```bash
sudo apt install exfatprogs
```

Format:

```bash
sudo mkfs.exfat -n MYUSB /dev/sdX1
```

Check:

```bash
lsblk -f
```

---

#  USB Mount Note (Manual Mount)

##  Mount Folder Create

```bash

sudo mkdir -p /mnt/myusb  ~/usb home folder ထဲတွင်လုပ်နိုင်သည် 

```

---

##  Mount (Recommended Options for exFAT)

```bash
sudo mount -t exfat -o uid=1000,gid=1000 /dev/sdX1 /mnt/myusb
```

- uid=1000 → your user
    
- gid=1000 → your group
    
- Permission error မဖြစ်အောင်
    

Check:

```bash
df -h
```

---

##  Unmount (Safely Remove)

```bash
sudo umount /mnt/myusb
```

- **Note**   Always unmount before unplug


---

#  Format Comparison

|Format|Android|Linux|Large Files|Use Case|
|---|---|---|---|---|
|exFAT|✅|✅|✅|Best cross-platform|
|FAT32|✅|✅|❌ 4GB limit|Old devices|
|ext4|❌|✅|✅|Linux only|

---

# Quick Workflow Summary

```
lsblk
fdisk /dev/sdX
mkfs.exfat /dev/sdX1
mount -t exfat -o uid=1000,gid=1000 /dev/sdX1 /mnt/myusb
copy files
umount /mnt/myusb
```

---
