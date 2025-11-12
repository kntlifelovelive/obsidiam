
---

## 🖥️ Disk & Storage Management Cheatsheet (Arch Linux / Hyprland)



##  Disk Usage Commands

### **1a. `df` – Filesystem space**

- **Purpose**: Disk partition တွေ size, usage, available space ကိုကြည့်ရန်
- **Command example**:


```bash
df -h
```

- **Explanation**:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       238G   96G  137G  42% /
```

- **Note**: `-h` = human-readable (GB, MB)


---

### **1b. `du` – Folder/file usage**

- **Purpose**: Folder, file space usage
- **Basic usage**:

```bash
du -sh /home/username/Videos
```

- **Options**:

```
-s : summary (total only)
-h : human-readable
-x : same filesystem only
--max-depth=N : depth level
```

- **Example**:

```bash
sudo du -xh --max-depth=1 / | sort -hr | head -20
```

- **Note**: Root folder ရဲ့ top usage directories ကို sort လုပ်ပြီးကြည့်နိုင်တယ်

---

### **1c. `duf` – Fancy CLI df**

- **Purpose**: `df` ကို visually prettier format နဲ့
- **Example**:

```bash
duf
```

- **Note**: Colorful bars, mount points, free/used space, easy visualization

---

### **1d. `ncdu` – ncurses du**

- **Purpose**: Interactive folder size analysis
- **Install**:

```bash
sudo pacman -S ncdu
```

- **Example usage**:

```bash
ncdu /home/username
```

- **Navigation**:    

```
Up/Down : select folder
Enter   : enter folder
d       : delete selected folder/file
q       : quit
```

- **Note**: Safe delete option built-in; `.cache` folder ကို clean လုပ်နိုင်တယ်

---

##  Snapper – Btrfs snapshots

### **2a. List snapshots**

```bash
sudo snapper -c home list
```

- **Options**:

```
-c <config> : snapshot configuration (root, home)
```

### **2b. Create snapshot**

```bash
sudo snapper -c home create -d "Before big changes"
```

- **Options**:

```
-d : description
```

### **2c. Delete snapshot**

```bash
sudo snapper -c home delete 3
```

- **Note**: Use snapshot number from list

### **2d. Auto snapshots**

- Auto snapshots by system events (pre/post update)
- **Disable auto**:

```bash
sudo systemctl stop snapper-timeline.timer
sudo systemctl disable snapper-timeline.timer
```

- **Note**: Timeline snapshots = automatic daily snapshots

---

##  Logs management (`/var/log`)

### **3a. Check log folder size**

```bash
sudo du -sh /var/log/*
```

### **3b. Journal cleanup**

```bash
sudo journalctl --vacuum-size=200M
sudo journalctl --vacuum-time=7d
```

- **Note**: Keeps log size under control

### **3c. Remove old/compressed logs**

```bash
sudo find /var/log -name "*.gz" -delete
sudo rm -rf /var/log/*.old
sudo truncate -s 0 /var/log/snapper.log
```

- **Note**: Do **not** delete `/var/log` folder entirely

---

##  Pacman Orphan Packages Cleanup

### **4a. List orphans**

```bash
sudo pacman -Qtdq
```

### **4b. Check sizes**

```bash
sudo pacman -Qtdq | xargs pacman -Qi | grep -E 'Name|Installed Size'
```

### **4c. Delete safe orphans**

```bash
sudo pacman -Rns $(pacman -Qtdq | grep -E 'debug|legacy|doc|moreutils|youtube-dl')
```

- **Note**: React/Web dev tools (electron, node, yarn, go) မဖျက်ရ

---

## 5️⃣ Cache Cleanup

### **5a. Pacman cache**

```bash
sudo pacman -Sc
```

- **Note**: Deletes old package files, keeps latest

### **5b. Yay/AUR cache**

```bash
yay -Sc
```

- **Note**: Deletes old AUR builds

### **5c. ncdu for `.cache`**

```bash
ncdu ~/.cache
```

- Delete unnecessary caches (browser, yay, etc.)

---

##  Summary / Notes

- **df** → disk partition usage
- **du** → folder/file usage
- **duf** → prettier df
- **ncdu** → interactive folder cleanup
- **snapper** → snapshots for Btrfs
- **journalctl** → logs vacuuming
- **pacman -Qtdq** → orphan packages
- **pacman/yay -Sc** → cache cleanup

**Tip**: Always check what is being deleted. Logs and cache are safe; orphan packages need attention if dev tools are used.

---

