
---

# 🔹 1. `pidof` (Process ID of a program)

**==> Run နေတဲ့ process ရဲ့ PID (process ID number) ကို ပြမယ်။  
အများအားဖြင့် _sysvinit_ systems (Debian, Ubuntu) မှာ default ပါလာတတ်တယ်။**

**Basic Example**

```bash
pidof sshd
```

➡ sshd process PID ကိုပြမယ်။ eg: `1025`

```bash
pidof bash
```

➡ လက်ရှိ run နေတဲ့ bash shell PID ကိုပြမယ်။


### Useful Options for `pidof`

- **`-s`** → first PID ကိုပဲ ပြမယ် (single result) ။ 
- **`-c`** → current shell session ထဲမှာမဟုတ်တဲ့ process တွေကိုပဲ ပြမယ် ။
- **`-o`** → specific PID ကို exclude လုပ်မယ် (ထုတ်မပြချင်တဲ့ PID) ။

**Examples:**

```bash
pidof -s bash
```

➡ bash ရဲ့ PID တစ်ခုတည်း ပြမယ်။

```bash
pidof -o %PPID bash
```

➡ လက်ရှိ shell ကို မပါဘဲ bash PID တွေပြမယ် (own parent process ကို skip).

```bash
pidof -c gnome-shell
```

➡ လက်ရှိ session ထဲက processes ကို မပါဘဲ PID ပြမယ်။

---

# 🔹 2. `pgrep` (Process Grep)

==> Pattern ကိုထည့်ပြီး running processes တွေကို PID အနေနဲ့ရှာပေးမယ်။  
`grep` လိုပဲပဲ၊ process name နဲ့ match ဖြစ်ရမယ်။

**Basic Example:**

```bash
pgrep ssh
```

➡ ssh ပါတဲ့ process PID တွေ အကုန် ပြမယ်။

```bash
pgrep -l bash
```

➡ PID + process name (`-l` = list with name)


### Useful Options for `pgrep`

- **`-l`** → PID နဲ့ process name လည်း ပြမယ်
- **`-a`** → full command line အကုန်ပြမယ်
- **`-u USER`** → သတ်မှတ်ထားတဲ့ user ရဲ့ process တွေကိုပဲရှာမယ်
- **`-P PID`** → parent PID ရဲ့ child processes တွေကိုရှာမယ်
- **`-n`** → newest (recently started) process PID
- **`-o`** → oldest process PID
- **`-d DELIM`** → delimiter တစ်ခုသတ်မှတ်ပြီး PID တွေကို တပေါင်းထုတ်မယ်

**Examples:**

```bash
pgrep -l firefox
```

➡ firefox process PID + name ပြမယ်။

```bash
pgrep -a ssh
```

➡ ssh process PID + full command line (path + options) ပြမယ်။

```bash
pgrep -u kyaw bash
```

➡ `kyaw` user ရဲ့ bash process တွေ ပြမယ်။

```bash
pgrep -P 1
```

➡ PID 1 (init/systemd) ရဲ့ child processes တွေ ပြမယ်။

```bash
pgrep -n bash
```

➡ အခုနောက်ဆုံး run လိုက်တဲ့ bash PID ကိုပဲ ပြမယ်။

```bash
pgrep -o bash
```

➡ အဟောင်းဆုံး run နေတဲ့ bash PID ကိုပဲ ပြမယ်။

```bash
pgrep -d , bash
```

➡ PID တွေကို comma-separated list အနေနဲ့ ပြမယ်။ eg: `1234,5678,9876`

---

### Key Difference (pidof vs pgrep)

|Command|Feature|
|---|---|
|**pidof**|အချို့ distro တွေမှာမပါတတ်, process name နဲ့ PID တွေကိုထုတ်ပေးတယ်|
|**pgrep**|grep style searching, option ပိုများ, PID နဲ့ name/command line/owner အကုန်ကြည့်လို့ရတယ်|

---
---
#### Homework (Practice)

1. `pidof bash` နဲ့ `pgrep bash` ကို နှိုင်းယှဉ်ပြီး output ကြည့်ပါ။
2. `pgrep -a python` နဲ့ python script ကို run ထားပြီး PID + command line ကြည့်ပါ။
3. Run နေတဲ့ `bash` process တွေကို `pgrep -u $(whoami) bash` နဲ့ ရှာပါ။
4. `tail -f /var/log/syslog` run ထားပြီး နောက်တစ်ဖက် terminal က `pidof tail` နဲ့ PID ကိုဖမ်းပါ။
---
---
---

## 🔹 Process ID (PID)

- Linux system မှာ အလုပ်လုပ်နေတဲ့ process တစ်ခုချင်းစီကို system က unique number (PID) တစ်ခု assign လုပ်ထားတယ်။
- PID က identity card လိုမျိုး — **process ကိုဖမ်းချင်ရင် PID သဘောပေါက်ဖို့လိုမယ်။**


**Example:**

```bash
pgrep -u $(whoami) bash
```

➡ ကိုယ့် user account (eg: kyaw) က run နေတဲ့ bash process PID တွေကိုပြမယ်။

```bash
pidof bash
```

➡ system ထဲမှာ bash PID အကုန်ပြမယ်။

 ဒီ ၂ ခုထဲက PID တွေ အများအားဖြင့် တူတူပေါ်တတ်တယ် (အချို့ system အပေါ်မူတည်ပြီး ခြားနိုင်တယ်)။

---

## 🔹 PID Management Importance

1. **Monitoring** → PID တွေကိုသိထားရင် process များကို check, track, debug လုပ်နိုင်မယ်။  
    Eg: `ps -p <PID>` နဲ့ PID တစ်ခုရဲ့ details ကိုကြည့်နိုင်မယ်။
2. **Killing/Stopping** → program တစ်ခု hang ဖြစ်သွားရင် PID ကိုသိရင် `kill <PID>` နဲ့ ရပ်နိုင်မယ်။
3. **Automation** → script ထဲမှာ process management တွေ လုပ်ဖို့ PID တွေကို အသုံးပြုမယ်။


## 🔹 Process Control Commands

## 1. `kill`

==> Specific PID ကို terminate (signal ပို့ပြီး stop) လုပ်မယ်။

**Basic Example:**

```bash
kill 1234
```

➡ PID 1234 process ကို stop လုပ်မယ် (default signal = `SIGTERM`).

---

### Signals with `kill`

- **`-15` (SIGTERM)** → Default, process ကို gracefully stop (အလုပ်ပြီးသွားအောင် ရပ်ခိုင်းတယ်
- **`-9` (SIGKILL)** → Force stop (no cleanup, immediately killed)
- **`-1` (SIGHUP)** → Reload (config reload, eg: web server)

**Examples:**

```bash
kill -15 1234
```

➡ PID 1234 ကို gracefully terminate

```bash
kill -9 1234
```

➡ PID 1234 ကို force kill

```bash
kill -1 1234
```

➡ PID 1234 ကို restart (config reload လိုမျိုး)

---

## 2. `pkill`

==> PID မသိဘဲ process name နဲ့ directly stop လုပ်နိုင်မယ်။

**Example:**

```bash
pkill firefox
```

➡ firefox process အကုန် stop လုပ်မယ်။

**Options:**

- `-u USER` → specific user ရဲ့ process ကိုပဲ stop
- `-n` → newest process ကိုပဲ stop
- `-o` → oldest process ကိုပဲ stop
- `-9` → force stop

**Examples:**

```bash
pkill -u kyaw bash
```

➡ `kyaw` user ရဲ့ bash process အကုန် stop

```bash
pkill -9 tail
```

➡ tail process ကို force stop


## 3. `killall`

==> Program name နဲ့ပဲ processes အကုန် stop လုပ်မယ်။  
`pkill` နဲ့တူပေမယ့်, system အလိုက် slightly different behavior ရှိတတ်တယ်။

**Example:**

```bash
killall firefox
```

➡ firefox processes အကုန် stop

**Options:**

- `-u USER` → specific user ရဲ့ processes ကိုပဲ stop
- `-i` → confirm before killing
- `-q` → quiet mode (no errors shown)


**Examples:**

```bash
killall -u kyaw bash
```

➡ `kyaw` ရဲ့ bash processes အကုန် stop

```bash
killall -i python
```

➡ python process ကို stop မယ်, confirm မေးမယ်

---

## Diffrient Type

|Command|What it uses|Usage|
|---|---|---|
|**kill**|PID|`kill -9 1234`|
|**pkill**|process name (pattern search)|`pkill firefox`|
|**killall**|exact process name|`killall firefox`|

---

## Homework (Practice Ideas)

1. `gedit` (သို့မဟုတ် text editor) ကို run ထားပြီး →
    - `pidof gedit` နဲ့ PID ကို ရှာပါ
    - `kill <PID>` နဲ့ stop လုပ်ပါ
2. Firefox (သို့မဟုတ် browser) ကို run ထားပြီး →
    - `pgrep firefox` နဲ့ PID ရှာပါ
    - `pkill firefox` နဲ့ stop လုပ်ပါ

3. Terminal ထဲမှာ process တစ်ခု `tail -f /var/log/syslog` run ထားပြီး →
    - terminal က `killall tail` နဲ့ stop လုပ်ပါ

 
**PID = process identity**  
**kill/pkill/killall = process ကို ရပ်/ထိန်းချုပ်ဖို့ အသုံးချတဲ့ နည်းလမ်း ၃ မျိုး**

---

