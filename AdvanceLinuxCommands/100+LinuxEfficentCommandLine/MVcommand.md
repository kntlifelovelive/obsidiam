
---

##  Note: `mv` command + pattern (extglob)

### 1. extglob ကို enable လုပ်ရမယ်

```bash
shopt -s extglob
```

---

### 2. Basic usage

- **Single folder ကိုချန်ထားပြီး အခြားအကုန်ရွှေ့ချင်ရင်**


```bash
mv !(keep) target_folder/
```

 - `keep/` ကို မရွှေ့ဘဲ အခြားအကုန်ကို `target_folder/` ထဲကိုရွှေ့မယ်

---

### 3. Multiple folders/files ချန်

- `@(a|b|c)` ဆိုတဲ့ pattern သုံးမယ်

```bash
mv !(@(keep1|keep2|logs|target1)) target1/

## This is  my test command line 
mv !(@(bubu.txt|dudu.txt|teti15)) teti15/ 
```


 - `keep1/`, `keep2/`, `logs/`, `target1/` မရွှေ့ဘဲ  
 - အခြား folder/file အကုန် `target1/` ထဲကိုရွှေ့မယ်

---

### 4. Pattern explanation

- `!(pattern)` → pattern 
- `@(a|b|c)` → `a` နဲ့ `b` နဲ့ `c` 
- `*` → wildcard, 
- `?` → 

---



---

 - Short summary:  
 - `mv !(keep) target/` = keep မဟုတ်တဲ့ အကုန် target ထဲ  
 - `mv !(@(a|b|c)) target/` = a,b,c မဟုတ်တဲ့ အကုန် target ထဲ

---

