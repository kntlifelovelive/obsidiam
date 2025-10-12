
##### 🔹 Linux Signal Handling
Linux process ကို control လုပ်ဖို့ system က signal ဆိုတဲ့ အမိန့်တွေ ပေးတတ်တယ်။  
`kill` command က process ကို “သတ်” တာမဟုတ်ပဲ **signal ပို့တာ** လိုက်နာရုံပါ။

---

## 1. `SIGTERM` (signal 15)

- Default signal (`kill <PID>` မှာ default = SIGTERM)
- **Graceful shutdown** → process ကို နူးညံ့စွာ ရပ်ခိုင်းတယ်, cleanup လုပ်နိုင်တယ်
- Eg: server application အများစုက config save, log close စပြီး အလုပ်ပြီးသွားအောင် stop လုပ်မယ်

**Example:**

```bash
kill -15 1234
```

➡ PID 1234 ကို gracefully terminate လုပ်မယ်။

---

## 2. `SIGKILL` (signal 9)

- **Force stop** → process ကို သတ်မယ် (cleanup မလုပ်နိုင်)
- system hang ဖြစ်တဲ့ app တွေ stop လုပ်ဖို့အတွက် သုံးတယ်


**Example:**

```bash
kill -9 1234
```

➡ PID 1234 ကို forcibly killed.

⚠️ သတိ – Data corruption ဖြစ်နိုင်တာကြောင့် **တကယ့်နောက်ဆုံးနည်း** အနေနဲ့ သုံးသင့်တယ်။


## 3. `SIGHUP` (signal 1)

- “Hangup” → traditionally terminal disconnect ကိုဆိုလိုတယ်
- modern usage → process ကို _reload config_ လုပ်ခိုင်းတယ်

**Example:**

```bash
kill -1 1234
```

➡ PID 1234 ကို config reload ခိုင်းမယ်။  
(eg: web server ကို restart မလုပ်ဘဲ config reload လုပ်ချင်တဲ့အချိန်)


## 🔹 Running Jobs in Shell

Linux shell (bash/zsh) မှာ background / foreground jobs ကို control လုပ်လို့ရတယ်။

## 4. `&` (Background Execution)

==> Command runပြီး terminal ကို တခြားအသုံးပြုချင်ရင် background လိုက်ပို့နိုင်မယ်။

**Example:**

```bash
gedit &
```

➡ gedit ကို background မှာ run, terminal ကိုလွတ်ပေးမယ်။

---

## 5. `jobs`

==> လက်ရှိ shell မှာ background/foreground jobs တွေကို စစ်မယ်။

**Example:**

```bash
jobs
```

➡ output:

```
[1]+  Running   gedit &
```


### 6. `fg` (Foreground)

==> Background job ကို foreground ပြန်ခေါ်မယ်။

**Example:**

```bash
fg %1
```

➡ job number 1 ကို foreground ပြန်ခေါ်မယ်။

---

### 7. `bg` (Background)

==> Stopped job ကို background မှာ run ထားမယ်။

**Example:**

```bash
sleep 100
# Ctrl+Z → stop job temporarily
bg %1
```

➡ job 1 ကို background မှာ ပြန် run မယ်။

### 🔹 8. `nohup` (No Hang Up)

==> Terminal ပိတ်သွားတောင် process ရပ်မသွားအောင် run ခိုင်းမယ်။

**Example:**

```bash
nohup python3 myscript.py &
```

➡ `myscript.py` ကို background မှာ run, terminal ပိတ်သွားလည်း ရပ်မသွားဘဲ ဆက် runမယ်။
Output က `nohup.out` file ထဲမှာ save ဖြစ်မယ်။

### Summary Table

|Command/Signal|Meaning|Example|
|---|---|---|
|`kill -15 PID`|Graceful terminate (SIGTERM)|`kill -15 1234`|
|`kill -9 PID`|Force kill (SIGKILL)|`kill -9 1234`|
|`kill -1 PID`|Reload config (SIGHUP)|`kill -1 1234`|
|`&`|Run command in background|`gedit &`|
|`jobs`|Show job list|`jobs`|
|`fg %n`|Bring job to foreground|`fg %1`|
|`bg %n`|Resume job in background|`bg %1`|
|`nohup`|Run even if terminal closes|`nohup command &`|

### Homework (Practice)

1. `sleep 60` run လုပ်ပြီး → `Ctrl+Z` နဲ့ stop → `bg` နဲ့ background ပြန်ထည့်ပါ → `jobs` နဲ့ စစ်ပါ။
2. `gedit &` run → `jobs` နဲ့ PID စစ် → `fg %1` နဲ့ foreground ပြန်ခေါ်ပါ။
3. `nohup ping google.com &` run → terminal ပိတ်ပြီး ပြန်ဖွင့် → `ps aux | grep ping` နဲ့ စမ်းပါ။
4. PID တစ်ခုကို `kill -15` နဲ့ stop လုပ်ပြီး, အရမ်း stubborn ဖြစ်တဲ့ process တစ်ခုကို `kill -9` နဲ့ force stop လုပ်ကြည့်ပါ။

---
