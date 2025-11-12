

---

##  `diff` Command 

=> File နှစ်ခု (သို့) Directory နှစ်ခုကြားက ဘယ်လိုကွာခြားမှုရှိတယ်ဆိုတာပြတယ်။

**Basic syntax:**

```bash
diff [options] file1 file2
```

---

##  Example 1 – Simple File Difference

ဖိုင်နှစ်ခုရှိတယ်ဆိုပါစို့:

**file1.txt**

```text
apple
banana
mango
```

**file2.txt**

```text
apple
orange
mango
```

**Command:**

```bash
diff file1.txt file2.txt
```

**Output:**

```
2c2
< banana
---
> orange
```

**Explain**

- `2c2` => line 2 မှာ change ဖြစ်တယ်။
- `< banana` => file1.txt မှာရှိတဲ့ line
- `> orange` =>  file2.txt မှာရှိတဲ့ line

---

##  Example 2 – Unified Format (Git style)

Git style လိုမျိုး unified format လိုချင်ရင် `-u` သုံးတယ်။

```bash
diff -u file1.txt file2.txt
```

**Output:**

```diff
--- file1.txt   2025-11-11
+++ file2.txt   2025-11-11
@@ -1,3 +1,3 @@
 apple
-banana
+orange
 mango
```

🔹 `-` ဆိုတာ remove  
🔹 `+` ဆိုတာ add

ဒီ format ကို `git diff` မှာပါသုံးပါတယ်။

---

## Example 3 – Directory Compare

folder နှစ်ခုကြားက file difference ကိုပါပြနိုင်တယ်။

```bash
diff -r dir1 dir2
```

**`-r`** ➡ recursive compare  
**Output:**

```
Only in dir2: newfile.txt
Files dir1/a.txt and dir2/a.txt differ
```

---

##  Example 4 – Ignore Case or Whitespace

ဖိုင်တွေက text အနည်းငယ်ကွာသွားတယ်ဆိုရင် လိုချင်တဲ့ option

|Option|အဓိပ္ပါယ်|
|:-:|:--|
|`-i`|case (A vs a) ignore|
|`-b`|space difference ignore|
|`-w`|all whitespace ignore|


```bash
diff -iw file1.txt file2.txt
```

---

##  Example 5 – Save Output to Patch File

`diff` result ကို later apply လုပ်ချင်ရင် `patch` file အနေနဲ့ save လုပ်လို့ရတယ်။

```bash
diff -u file1.txt file2.txt > change.patch
```

ပြီးရင် apply လုပ်ချင်ရင်

```bash
patch file1.txt < change.patch
```

ဒါဆို file1.txt ကို file2.txt အတိုင်းပြောင်းသွားမယ်။

---

## Summary Table

|Command|Description|
|---|---|
|`diff file1 file2`|Compare 2 files|
|`diff -u file1 file2`|Unified diff (Git-style)|
|`diff -r dir1 dir2`|Compare directories|
|`diff -i`|Ignore case|
|`diff -w`|Ignore spaces|
|`diff -u old new > patch.diff`|Create patch file|
|`patch old < patch.diff`|Apply patch|

---

