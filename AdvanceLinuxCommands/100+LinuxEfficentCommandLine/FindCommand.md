
---

### Find command 
```bash
find . ! -name 'keep.txt' -type f -delete
```



### Main Syntax 

- `find .` ==> လက်ရှိ directory ( `.` ) အောက်မှာ ရှာမယ်
- `! -name 'keep.txt'` ==> `keep.txt` ဆိုတဲ့ အမည်မဟုတ်သမျှကို ရွေးမယ်
- `-type f` ==> ဖိုင် (file) ကိုပဲရွေးမယ် (folder မထိ)
- `-delete` ==> ရွေးထားတဲ့ ဖိုင်တွေကို delete လုပ်မယ်
- အဆိုပါ command က **လက်ရှိ directory အောက်ရှိ အားလုံး file တွေကိုဖျက်ပြီး `keep.txt` တစ်ခုကိုသာချန်ပေးမယ်** 




#### 1. **Folder အပါအဝင် ဖျက်ချင်ရင်**

```bash
find . ! -name 'keep.txt' -delete
```

- ==> `-type f` မထည့်တာကြောင့် directory ပါ ဖျက်မယ် ( `keep.txt` ကိုပဲမထိ)



#### 2. **delete မလုပ်သေးခင် (test only)**

```bash
find . ! -name 'keep.txt' -type f -print
```

- ==> ဖျက်မယ့် ဖိုင်နာမည်တွေကို အရင် print ပြပေးမယ်



#### 3. **Folder ကို ထိစေချင် / မထိစေချင်**

- ဖိုင်ပဲ ဖျက်မယ် ==> `-type f`
- folder ပဲ ဖျက်မယ် ==> `-type d` 
- file + folder အကုန် ဖျက်မယ် ==>  -type f or d မထည့်ပဲ 



#### 4. **အမျိုးအစားအလိုက် filter လုပ်ချင်ရင်**

- `.txt` မဟုတ်တာ ဖျက်ချင်

```bash
find . ! -name '*.txt' -type f -delete
```

- `.log` ဖိုင်ပဲ ဖျက်ချင်

```bash
find . -name '*.log' -type f -delete
```



#### 5. **အရွယ်အစားအလိုက် filter**

- 1MB ထက်ကြီးတဲ့ဖိုင် ဖျက်မယ်

```bash
find . -type f -size +1M -delete
```

- 100KB ထက်သေးတဲ့ဖိုင် ဖျက်မယ်

```bash
find . -type f -size -100k -delete
```



#### 6. **အချိန်အလိုက် filter**

- 7 ရက်ထက်အိုတဲ့ဖိုင် ဖျက်မယ်

```bash
find . -type f -mtime +7 -delete
```

- နာရီ 1 ထဲက ဖိုင်ပဲ ဖျက်မယ်

```bash
find . -type f -mmin -60 -delete
```



#### 7. **စစ်ပြီးမှ confirm နဲ့ ဖျက်ချင်ရင်**

```bash
find . ! -name 'keep.txt' -type f -ok rm {} \;
```

- ==> ဖိုင်တိုင်း ဖျက်မလား မဖျက်ဘူးလား confirm မေးမယ် (yes/no)



### Note

`find` command flexible 

- `-name` (name filter)
- `-type` (file / directory)
- `-size` (file size)
- `-mtime` / `-mmin` (modified time)
- `-delete`, `-print`, `-exec`, `-ok` (action)
---
