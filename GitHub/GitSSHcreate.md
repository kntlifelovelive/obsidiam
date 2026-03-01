

---

#  SSH key Check

```bash
ls ~/.ssh
```

`id_ed25519` နဲ့ `id_ed25519.pub` ရှိရင် already key ရှိတယ် ✔️  
မရှိရင် new key generate လုပ်မယ်။

---

#  New SSH Key Generate 

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

==> `your_email@example.com` ကို **GitHub email** နဲ့ပြောင်းပါ။

Enter ၃ ခါနှိပ်လိုက်ရုံပဲ  
(default location OK)

Generate ပြီးရင် ဒီလိုဖိုင် ၂ ခု ရမယ် 

```
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

---

#  SSH Agent Start 

```bash
eval "$(ssh-agent -s)"
```

ပြီးရင် key add လုပ်မယ် 

```bash
ssh-add ~/.ssh/id_ed25519
```

---

# Public Key Copy 

```bash
cat ~/.ssh/id_ed25519.pub
```

Output ကို **copy all** လုပ်ပါ (ssh-ed25519 နဲ့စတဲ့ line)

---

#  GitHub မှာ Key ထည့်မယ်

1. GitHub ဝင်ပါ
    
2. Profile ➜ Settings
    
3. **SSH and GPG keys**
    
4. **New SSH Key**
    
5. Title ထည့် (eg. ArchLaptop)
    
6. Paste public key
    
7. Save ✔️
    

---

#  Connection Test လုပ်မယ်

```bash
ssh -T git@github.com
```

ဒီလိုထွက်ရမယ် 

```
Hi username! You've successfully authenticated...
```

ဒါဆို OK ပြီ ။

---

#  Git Remote ကို SSH ပြောင်း (မပြောင်းရသေးရင်)

```bash
git remote set-url origin git@github.com:username/repo.git
```

---

#  Push check 

```bash
git push
```

Password မမေးတော့ဘူး ✔️  
SSH key နဲ့ auto login ဖြစ်သွားမယ်။

---

