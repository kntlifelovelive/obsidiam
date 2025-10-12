
---
`rm -rf` သုံးတဲ့အခါ `!` (negation) နဲ့ `find` သုံးမယ်။

`keep.txt ` ဖိုင်ကိုမဖျက်ပဲ ကျန်တာအားလုံးဖျက်ချင်ရင်။

```bash
find . ! -name 'keep.txt' -type f -delete
```

### Mode 

- `find .`  လက်ရှိ directory အောက်မှာရှာမယ်
- `! -name 'keep.txt'` ==> `keep.txt` ကိုမထိပါနဲ့
- `-type f` ဖိုင်တွေကိုသာ ရွေးမယ်
- `-delete`  ဖျက်မယ်

Folder or folder ဖျက်ချင်ရင် (directory အပါအဝင်)

```bash
find . ! -name 'keep.txt' -delete
```


###  `rm -rf`  glob pattern 
**Global Pattern**
- Terminal in first command `shopt -s extglob` 
```bash
shopt -s extglob

rm -rf !(keep.txt)
```

*Note* ဒီနည်းက bash shell ထဲမှာပဲ အလုပ်လုပ်မယ်၊ `keep.txt` အပြင် အကုန်ဖျက်မယ်။

---
