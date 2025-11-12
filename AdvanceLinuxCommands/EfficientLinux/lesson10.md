

---

# Disk Management & Filesystem Tools

### 1 Understanding Filesystems

 **Filesystem** 
> Storage device (SSD/HDD/USB) အပေါ် data တွေကို structure ပေးဖို့အတွက် Linux က အသုံးပြုတဲ့ organizing method ပဲ။

**Popular Linux Filesystems:**

|Type|Description|
|---|---|
|`ext4`|Default, stable, journaling|
|`xfs`|High-performance filesystem|
|`btrfs`|Modern, snapshot & compression|
|`vfat`|Compatible with Windows FAT|
|`ntfs`|Windows filesystem support|
|`tmpfs`|Temporary memory filesystem (RAM-based)|


**Diagram (Concept):**

```
Disk → Partition → Filesystem → Mount Point (/home, /boot, etc)
```


### Viewing Disk Usage

#### **`df` – Display Filesystem Usage**

**Syntax:**

```bash
df [options]
```

|Option|Description|
|---|---|
|`-h`|human-readable sizes (MB/GB)|
|`-T`|show filesystem type|
|`-a`|include all filesystems|



**Example 1 – check all mounted disks:**

```bash
df -h
```

➡ Shows disk usage with readable format.

**Example 2 – show filesystem type:**

```bash
df -Th
```

➡ Displays mount points, size, usage, and FS type.

 **Example Output:**

```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4   50G   25G   23G  53% /
tmpfs          tmpfs 2.0G  1.2M  2.0G   1% /run
```


### **`du` – Display Directory/File Size**

**Syntax:**

```bash
du [options] [path]
```

|Option|Description|
|---|---|
|`-h`|human-readable|
|`-s`|summary only|
|`--max-depth=1`|show size by directory level|


**Example 1 – total size of folder:**

```bash
du -sh /home/kyaw/
```

**Example 2 – show folder-by-folder breakdown:**

```bash
du -h --max-depth=1 /var/log/
```

 Diagram:

```
/var/log/
├── apache2 → 200M
├── syslog  → 50M
└── kern.log → 10M
```


###  Mounting & Unmounting Devices

> Linux မှာ storage device တစ်ခုကို သုံးချင်ရင် ပထမဆုံး “mount” လုပ်ဖို့လိုတယ်။

**View all block devices:**

```bash
lsblk
```

Example Output:

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0  120G  0 disk 
├─sda1   8:1    0  512M  0 part /boot
└─sda2   8:2    0  119G  0 part /
sdb      8:16   1   16G  0 disk 
└─sdb1   8:17   1   16G  0 part 
```


### **Mount Device**

```bash
sudo mount /dev/sdb1 /mnt/usb
```

### **Unmount Device**

```bash
sudo umount /mnt/usb
```

**Check mounted drives:**

```bash
mount | grep /mnt
```

 _Tip:_ `/etc/fstab` file ထဲမှာ permanent mount configuration ထည့်လို့ရတယ်။

---

### 4 Checking Disk Health – `fsck`

 **File System Consistency Check**  
Filesystem corrupt ဖြစ်တာတွေကို scan & repair လုပ်ဖို့သုံးတယ်။

**Syntax:**

```bash
sudo fsck /dev/sda2
```

 Run only on _unmounted_ partitions (e.g., from recovery mode).


 **Diagram (Concept):**

```
/dev/sda2  → fsck scan → found errors → fix them
```



###  Finding Which Process Uses a File or Port

#### **`lsof` – List Open Files**

**Syntax:**

```bash
lsof [options]
```

|Option|Description|
|---|---|
|`-u username`|show files by user|
|`+D /path`|show files under directory|
|`-i :PORT`|show processes using port|


**Example 1 – find who uses a file:**

```bash
sudo lsof /var/log/syslog
```

**Example 2 – check port usage:**

```bash
sudo lsof -i :8080
```

➡ Shows process (PID) using port 8080.

**Example 3 – list all open files by current user:**

```bash
lsof -u $(whoami)
```


### **`fuser` – Identify Processes Accessing Files**

```bash
sudo fuser -v /var/log/syslog
```

➡ Displays which process is using that file.

**Kill process using a file:**

```bash
sudo fuser -k /mnt/usb
```



## 6 Disk Partition Management

> `fdisk`, `lsblk`, `parted`, `blkid` တို့က physical partition management tool တွေ။

**View partition table:**

```bash
sudo fdisk -l
```

**Get UUID & filesystem info:**

```bash
blkid
```

Example:

```
/dev/sda1: UUID="a1b2-c3d4" TYPE="ext4" PARTUUID="abcd-01"
```

 _Tip:_ UUID ကို `/etc/fstab` ထဲမှာ mount permanent entry အနေနဲ့ အသုံးပြုတယ်။



### 7 Disk Space Analysis – `ncdu` (Bonus)

 Interactive text-based disk analyzer (faster than du).  
Install with:

```bash
sudo apt install ncdu 

# or Arch linux 

sudo pacman -S ncdu 
```

Run:

```bash
ncdu /
```

➡ browse disk usage visually & delete unused files interactively.

 Diagram:

```
[ ncdu view ]
/home/kyaw/
├── Downloads (1.2G)
├── Videos (10G)
└── Documents (500M)
```



###  Summary Table

|Command|Purpose|Example|
|---|---|---|
|`df -h`|Disk space overview|`df -h`|
|`du -sh`|Directory size|`du -sh /var`|
|`lsblk`|List block devices|`lsblk`|
|`mount / umount`|Mount or unmount device|`sudo mount /dev/sdb1 /mnt/usb`|
|`fsck`|Check & repair filesystem|`sudo fsck /dev/sda2`|
|`lsof`|Show open files|`lsof -i :22`|
|`fuser`|Identify users of file|`fuser -v /mnt`|
|`fdisk -l`|Partition table info|`sudo fdisk -l`|
|`blkid`|Show UUID|`blkid`|
|`ncdu`|Disk usage analyzer|`ncdu /home`|

---

### Homework (Disk Lab Challenge)

1. `df -h` နဲ့ mounted filesystem တွေကို စစ်ပါ။
2. `/home` folder size ကို `du -sh /home` နဲ့ စစ်ပါ။
3. `/dev/sdb1` USB ကို `/mnt/usb` မှာ mount လုပ်ပြီး file တစ်ခု copy လုပ်ပါ။
4. `lsof -i :80` နဲ့ port 80 ကို အသုံးပြုနေသူကို ရှာပါ။
5. `sudo fsck /dev/sda2` ကို recovery mode မှာ run လုပ်ကြည့်ပါ။
6. Bonus  – `ncdu /var` သုံးပြီး log folder တန်ဖိုးကြီးဆုံး file ကို delete လုပ်ပါ။


---

 

