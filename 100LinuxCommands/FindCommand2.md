
---


### File & Folder Count Command 

##### 1. **File + Folder အားလုံး count**

```bash
ls -1 | wc -l
```

- `ls -1` ==> line တစ်ကြောင်းချင်းစီ file/folder ပြပေးမယ်
- `wc -l` ==> line အရေအတွက်တွက်ပေးမယ်

---

### 2. **File အရေအတွက်ပဲ (Folder မပါ)**

```bash
find . -type f | wc -l
```

- `find . -type f` ==> လက်ရှိ directory အောက်က file တွေကိုပဲ ရှာမယ် 
- `wc -l` ==>  အရေအတွက်တွက်ပေးမယ်

---
##### 3. **Folder အရေအတွက်ပဲ (File မပါ)**

```bash
find . -type d | wc -l
```

`.` directory ကိုလည်းပါမယ်၊ လက်ရှိ folder ကိုပါမသိချင်ရင် 

```bash
find . -mindepth 1 -type d | wc -l
```

---

##### 4. **File နဲ့ Folder ကိုအမျိုးအစားခွဲပြီး count**

```bash
echo "Files: $(find . -type f | wc -l)"
echo "Folders: $(find . -type d | wc -l)"
```

---

##### 5. **Hidden file/folder တွေလည်း တွက်ချင်ရင်**

```bash
ls -A1 | wc -l
```

---

*Example*

```bash
Files: 120
Folders: 15
```

---
