
---

## Basic Package Management Commands (Arch Linux )

### 1. **System Update (Full upgrade)**

```bash
sudo pacman -Syu
```


- **S** → Sync (repository နဲ့ sync လုပ်မယ်)
- **y** → Refresh database (package list အသစ်ယူမယ်)
- **u** → Upgrade installed packages (အသစ် version ထွက်တာ upgrade လုပ်မယ်)
 `-Syu` ဆိုတာဟာ "database refresh + upgrade" အနေနဲ့ သုံးတာပါ။  
 
Example:

```
:: Synchronizing package databases...
:: Starting full system upgrade...
```

---

### 2.  **Install package**

```bash
sudo pacman -S package_name
```

Example:

```bash
sudo pacman -S firefox
```

Firefox ကို install လုပ်မယ်။  
ပေါင်းစပ်ထည့် install လည်းရတယ်

```bash
sudo pacman -S firefox vlc gimp
```

---

### 3.  **Remove package**

```bash
sudo pacman -R package_name
```

=> အဲ့ဒါက basic remove ပါ။  
Package ကိုပဲဖျက်ပြီး dependency မဖျက်ပါဘူး။

---

### 4.  **Remove package with dependencies**

```bash
sudo pacman -Rs package_name
```

- **R** → remove
- **s** → remove unused dependencies (သုံးမဲ့ dependency လည်းဖျက်)

Example:

```bash
sudo pacman -Rs vlc
```

---

### 5.  **Remove package + config files**

```bash
sudo pacman -Rns package_name
```

=> **n** ဆိုတာ config files ပါဖျက်မယ်။  
Example:

```bash
sudo pacman -Rns firefox
```

 ဒီလိုလုပ်ရင် `/etc` ထဲမှာရှိတဲ့ setting file လည်းဖျက်သွားမယ်။

---

### 6.  **Reinstall package**

```bash
sudo pacman -S package_name --overwrite '*'
```

သို့မဟုတ် Or 

```bash
sudo pacman -S package_name
```

 `-S` သုံးပြီး ထပ် install လုပ်တာကို pacman က reinstall လုပ်ပေးတတ်တယ်။

Example:

```bash
sudo pacman -S vim
```

=> vim ရှိပြီးသားဆိုရင် reinstall လုပ်သွားမယ်။

---

### 7.  **Remove orphan packages (မသုံးတော့တဲ့ dependency)**

```bash
sudo pacman -Rns $(pacman -Qtdq)
```

 မသုံးတော့တဲ့ dependency (အကြောင်းမဲ့ပဲကျန်နေတဲ့ package) တွေဖျက်မယ်။

---

### 8.  **Search packages**

```bash
pacman -Ss name
```

Example:

```bash
pacman -Ss firefox
```

---

### 9.  **List installed packages**

```bash
pacman -Q
```

=> သင့်စက်ထဲမှာရှိတဲ့ package အားလုံး ပြမယ်။

Specific package ရှိ/မရှိ စစ်ချင်ရင်:

```bash
pacman -Q firefox
```

---

### 10.  **View package info**

```bash
pacman -Qi package_name
```

=> install date, version, size, dependency စတာတွေကြည့်လို့ရတယ်။

---

### Bonus Notive

အချို့အခါ pacman database error ဖြစ်တတ်တယ်

```bash
sudo pacman -Syyu # မသုံးသင့်ပါ
```

=> Double `y` ဆိုတာက force refresh database ဖြစ်တယ်။

---

