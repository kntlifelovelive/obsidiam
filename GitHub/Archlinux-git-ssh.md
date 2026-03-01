


GitHub ကို SSH နဲ့ ချိတ်ဖို့ **complete setup note Arch - Linux**

---
## Notice Note 

- first time terminal 

```bash 

git config --global user.name "kntlifelovelive"
git config --global user.email "kyawnyeinthant2010@gmail.com"

```

# GitHub SSH Setup Guide (Linux)

## 1.  SSH key ရှိ/မရှိ စစ်မယ်

```bash
ls -al ~/.ssh
```

`id_ed25519` သို့မဟုတ် `id_rsa` ရှိရင် already key ရှိတယ်။  
မရှိရင် အသစ် generate လုပ်မယ်။

---

## 2.SSH Key Generate လုပ်မယ်

Recommended → **ed25519**

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

- `your_email@example.com` ကို GitHub email နဲ့ပြောင်း

Enter → Enter → Enter (default path သုံးလို့ရတယ်)

Generate ပြီးရင် file တွေ:

```
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

---

## 3. SSH Agent Start လုပ်မယ်

```bash
eval "$(ssh-agent -s)"
```

Key add လုပ်မယ်:

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## 4.Public Key ကို Copy လုပ်မယ်

```bash
cat ~/.ssh/id_ed25519.pub
```

Output ထွက်လာတဲ့ `ssh-ed25519 AAAA....` ကို copy လုပ်။

---

## 5. GitHub ထဲမှာ Add လုပ်မယ်

Account login and -> GitHub → Settings → SSH and GPG keys → New SSH Key
Title Name Create → (eg. Arch Laptop)  
Key → paste လုပ်  
Save

---

## 6. Connection Test

```bash
ssh -T git@github.com
```

First time ဆိုရင်:

```
Are you sure you want to continue connecting?
```

→ `yes` ရိုက်

Success ဖြစ်ရင် message:

```
Hi username! You've successfully authenticated...
```

---

# Optional (Recommended) ~/.ssh/config

Multiple account သုံးရင် useful 

```bash
nano ~/.ssh/config
```

ထဲမှာထည့်:

```
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
```

Save → exit

Permission fix:

```bash
chmod 600 ~/.ssh/config
```

---

# Existing Repo ကို HTTPS ကနေ SSH ပြောင်းချင်ရင်

Check remote:

```bash
git remote -v
```

Change to SSH:

```bash
git remote set-url origin git@github.com:username/repo.git
```

Example:

```bash
git remote set-url origin git@github.com:archibubu/dotfiles.git
```

---

#  Debug မရရင်

```bash
ssh -vT git@github.com
```

Verbose mode ဖြစ်လို့ error detail မြင်ရမယ်။

---

# Summary

✔ ssh-keygen  
✔ ssh-add  
✔ GitHub မှာ key add  
✔ ssh -T test  
✔ git remote ssh change

---

