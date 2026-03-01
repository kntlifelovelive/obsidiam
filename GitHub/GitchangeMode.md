

---

## Step 1:  remote စစ်မယ်

```bash
git remote -v
```

ဒီလိုထွက်လာနိုင်တယ် ။ 

```bash
origin  https://github.com/kntlifelovelive/hyprbuti.git (fetch)
origin  https://github.com/kntlifelovelive/hyprbuti.git (push)
```

---

## Step 2: HTTPS ➜ SSH ပြောင်းမယ်

```bash
git remote set-url origin git@github.com:kntlifelovelive/hyprbuti.git
```

=> `origin` ဆိုတာ remote name ဖြစ်တယ်  
=> `set-url` က URL ကိုပြောင်းတာ

---

##  Step 3: ပြောင်းပြီးမပြီးစစ်မယ်

```bash
git remote -v
```

ဒီလိုဖြစ်ရမယ် 

```bash
origin  git@github.com:kntlifelovelive/hyprbuti.git (fetch)
origin  git@github.com:kntlifelovelive/hyprbuti.git (push)
```

---

##  Step 4: Push စမ်းကြည့်

```bash
git push
```

---

##  Important

SSH key မထည့်ရသေးရင် error တက်မယ် ❗  
စစ်ချင်ရင် 

```bash
ssh -T git@github.com
```

Welcome message ထွက်ရင် အိုကေပြီ။

---

##  Extra Knowledge (Pro Level)

Remote ကို rename လုပ်ချင်ရင် 

```bash
git remote rename origin newname
```

Remote ဖျက်ချင်ရင် 

```bash
git remote remove origin
```

---

