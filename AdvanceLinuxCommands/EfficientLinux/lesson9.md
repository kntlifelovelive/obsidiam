
---

# Process Management & Monitoring


## 1 What is a Process?

Process ဆိုတာ
> Linux kernel မှာ run နေပေမယ့် program တစ်ခုကို _instance_ အနေနဲ့ ပြုလုပ်ထားတဲ့ တန်ဖိုးပါ process ဖြစ်တယ်။

**Example:**

- Firefox ကိုဖွင့်လိုက်ရင် process တစ်ခုဖြစ်တယ်
- Background download (wget) က process တစ်ခုဖြစ်တယ်
- Terminal command တစ်ခုစလုံးက process တစ်ခုဖြစ်တယ်

##  Process Basics Commands

|Command|Purpose|
|---|---|
|`ps`|show running processes|
|`top`|monitor real-time usage|
|`htop`|visual interactive process viewer|
|`pidof`|find process ID by name|
|`pgrep`|pattern-based PID search|
|`kill`, `pkill`|terminate processes|
|`nice`, `renice`|adjust process priority|
|`jobs`, `fg`, `bg`|manage background/foreground jobs|


### 3 Viewing Processes with `ps`

**Syntax:**

```bash
ps [options]
```

**Common Options**

|Option|Description|
|---|---|
|`-e`|all processes|
|`-f`|full format|
|`-u username`|user-specific|
|`-ef`|detailed full list|

**Example 1 – show current terminal processes**

```bash
ps
```

**Example 2 – show all system processes**

```bash
ps -ef
```

**Example 3 – show processes for a user**

```bash
ps -u $(whoami)
```

**Example 4 – show hierarchy (parent-child)**

```bash
ps -ef --forest
```

 **Diagram:**

```
PID  PPID  CMD
100   1     systemd
120   100   bash
130   120   vim
```



### 4 Real-Time Monitoring with `top` & `htop`

### `top`

```bash
top
```

➡ CPU, Memory usage, Process IDs, User, etc... တို့ကို Live ပြတယ်။

**Keys inside `top`:**

|Key|Action|
|---|---|
|`q`|quit|
|`k`|kill process|
|`P`|sort by CPU|
|`M`|sort by memory|
|`u`|filter by user|

---

### `htop` (better interface)

 `sudo apt install htop` (Debian/Kali/Mint)

```bash
htop
```

- scroll horizontally/vertically
- sort by CPU, MEM, PID easily
- kill/nice by pressing `F9`, `F7`, `F8`


 **Diagram (htop):**

```
PID   USER   %CPU  %MEM  COMMAND
1045  kyaw    12.3  2.1   firefox
1123  kyaw     3.0  1.0   bash
```


### 5 Process Priority: `nice` & `renice`

> Linux မှာ process တစ်ခု run မယ်ဆိုရင် priority (nice value) တန်ဖိုးရှိတယ်။

|Range|Meaning|
|---|---|
|`-20`|highest priority|
|`0`|default|
|`+19`|lowest priority|


**Run process with specific priority:**

```bash
nice -n 10 ./heavy_task.sh
```

➡ low priority နဲ့ run မယ်။

**Change running process priority:**

```bash
renice -n -5 -p 1234
```

➡ PID 1234 process ကို higher priority ပေးမယ်။

 **Diagram:**

```
Priority ↑   (-20 ... +19)
   High ← kernel scheduler → Low
```

 _Tip:_  
Lower nice value → faster CPU attention.  
Higher value → runs slower but frees system.


### 6 Killing Processes

**Find process ID:**

```bash
pidof firefox
```

➡ returns PID (e.g., `2145`)

**Kill process:**

```bash
kill 2145
```

➡ sends default `SIGTERM` (graceful stop)

**Force kill (no mercy ):**

```bash
kill -9 2145
```

➡ sends `SIGKILL` (immediate stop)

**Kill by name:**

```bash
pkill firefox
```

**Kill all by pattern:**

```bash
pkill -f "python script.py"
```



### Signal Types (Most Common)

|Signal|Name|Description|
|---|---|---|
|`1`|SIGHUP|restart process|
|`9`|SIGKILL|force kill (cannot catch)|
|`15`|SIGTERM|normal terminate|
|`19`|SIGSTOP|pause process|
|`18`|SIGCONT|continue paused process|


**Diagram:**

```
Process (running)
   ↑ SIGTERM  → Graceful Exit
   ↑ SIGKILL  → Immediate Stop
   ↑ SIGSTOP  → Suspended
   ↑ SIGCONT  → Resumed
```


### 7 Background & Foreground Jobs

>CLI မှာ command တစ်ခုကို background / foreground အနေနဲ့ run လို့ရတယ်။

**Run in background:**

```bash
long_task.sh &
```

**View jobs:**

```bash
jobs
```

**Move to foreground:**

```bash
fg %1
```

**Pause process (Ctrl+Z) → move to background**

```bash
bg %1
```



 **Diagram:**

```
[Terminal] → launch process → (Ctrl+Z) → Suspended → bg → Running in background
```


### 8 nohup & disown

> Background jobs ကို terminal ပိတ်သွားလည်း  ဆက် run စေဖို့။

**Example:**

```bash
nohup python3 script.py &
```

➡ logout လုပ်လည်း run နေတာပဲ။

**Remove job link (so it’s safe):**

```bash
disown %1
```

 **Diagram:**

```
Terminal X (closed)
      ↓
nohup process → keeps running independently
```


### 9 Process Tree Visualization

**See parent-child relationship:**

```bash
pstree -p
```

Example Output:

```
systemd(1)─┬─NetworkManager(600)
            ├─sshd(700)───bash(900)
            └─chrome(1200)
```


###  Summary Table

|Command|Purpose|Example|
|---|---|---|
|`ps -ef`|list all processes|`ps -ef|
|`top` / `htop`|real-time monitoring|`top`, `htop`|
|`pidof`|find PID|`pidof bash`|
|`pgrep`|pattern search|`pgrep -u kyaw bash`|
|`kill`|terminate by PID|`kill -9 2345`|
|`pkill`|terminate by name|`pkill firefox`|
|`nice`|start process w/ priority|`nice -n 10 ./task.sh`|
|`renice`|change running priority|`renice -n -5 -p 1234`|
|`jobs`|list background jobs|`jobs`|
|`fg` / `bg`|move jobs|`fg %1`, `bg %2`|
|`nohup`|keep running after logout|`nohup ./script.sh &`|

### Homework (Process Lab Challenge)

1. `sleep 500 &` ကို run လိုက်ပြီး `jobs`, `ps`, `fg`, `bg` တွေသုံးကြည့်ပါ။
2. Firefox PID ကို `ps -ef | grep firefox` နဲ့ရှာပြီး `kill -15 PID` နဲ့ graceful stop လုပ်ပါ။
3. Script တစ်ခုကို `nice -n 15` နဲ့ run လိုက်ပြီး CPU usage ကို `htop` နဲ့ ကြည့်ပါ။
4. Background job တစ်ခုကို `disown` လုပ်ပြီး terminal ပိတ်ပါ။
5. Bonus  – `pstree -p` သုံးပြီး parent-child structure ကို diagram တစ်ခုပြပါ။


---
