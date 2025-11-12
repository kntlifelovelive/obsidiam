
အိုဟ့် 🥰 ကိုရေ တော်တယ်ဗျ — အခုတော့ Lesson 11 ရဲ့ **Part 4** 😎  
နာမည်ကြီး command နှစ်ခုဖြစ်တဲ့ 👉 **`traceroute`** နဲ့ **`tracepath`** ပိုင်းကို  
အပြည့်အစုံနဲ့သွားကြရအောင်နော် 🌍✨

ဒီ command နှစ်ခုပဲ _Network Path Diagnosis Tools_ တို့ဖြစ်ပြီး  
packet တစ်ခုက ဘယ် router, ISP, gateway လမ်းကြောင်းတစ်လျှောက်ဖြတ်သွားတယ်ဆိုတာ  
သိစေနိုင်တယ်ရှင့် 🚀

---

# 🌐 Lesson 11 – Part 4

## 🧩 `traceroute` & `tracepath` — Route Analysis (Mastery Level)

---

## 🧠 Basic Idea

`ping` ကတော့ host “alive or not” ကို စစ်တယ်။  
`traceroute` နဲ့ `tracepath` ကတော့ “packet ဘယ်လိုလမ်းကြောင်းဖြတ်သွားသလဲ” ဆိုတာကို ပြတယ်။

---

## 🔹 1️⃣ `traceroute` Command

### 📘 Syntax

```bash
traceroute [OPTIONS] destination
```

---

### 📊 Example Output

```bash
traceroute to google.com (142.250.191.78), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.263 ms  1.236 ms  1.214 ms
 2  10.0.0.1 (10.0.0.1)  10.527 ms  10.502 ms  10.477 ms
 3  203.81.81.1 (203.81.81.1)  15.231 ms  15.208 ms  15.184 ms
 4  172.217.161.142 (142.250.191.78)  22.367 ms  22.341 ms  22.317 ms
```

---

### 🧩 Explanation

|Column|Meaning|
|---|---|
|`1, 2, 3, ...`|Hop number (each router between you & destination)|
|`192.168.1.1`|IP of router/gateway|
|`(192.168.1.1)`|Reverse DNS name (if available)|
|`ms`|Round-trip time per probe|
|`* * *`|Request timed out (packet dropped)|

---

### 💡 What’s Happening Internally

Traceroute sends **UDP packets** (by default)  
→ each with **increasing TTL (Time To Live)**  
→ each router decrements TTL by 1 and sends back an ICMP “Time Exceeded” message  
→ tool records router IP → next hop → next hop → until destination reached ✅

---

### 📊 Diagram

```
[Your PC]
   │
   ▼
(1) 192.168.1.1   ← Home Router
   │
   ▼
(2) 10.0.0.1      ← ISP Gateway
   │
   ▼
(3) 203.81.81.1   ← Regional ISP Router
   │
   ▼
(4) 142.250.191.78 ← Google Server 🌍
```

---

### 🧩 Example 2 — Traceroute with ICMP Mode

```bash
sudo traceroute -I google.com
```

➡ Use ICMP Echo instead of UDP (like Windows `tracert`).

---

### 🧩 Example 3 — Specify Packet Size

```bash
traceroute -q 2 -w 3 -m 20 -p 33434 google.com
```

|Option|Meaning|
|---|---|
|`-q 2`|Number of probe packets per hop|
|`-w 3`|Timeout wait (seconds)|
|`-m 20`|Max hops (default 30)|
|`-p`|Starting UDP port|

---

### 🧩 Example 4 — Trace without DNS Resolution

```bash
traceroute -n google.com
```

➡ Show only IPs (no hostnames).

---

### 🧩 Example 5 — Save Output

```bash
traceroute google.com | tee trace_log.txt
```

➡ Log results for later analysis.

---

### 🧩 Example 6 — Trace to Local Network

```bash
traceroute 192.168.1.100
```

➡ Good for LAN route debugging.

---

## 🔹 2️⃣ `tracepath` Command

💡 `tracepath` ကတော့ traceroute နဲ့ ဆင်တယ်။  
➡ Root permission မလို  
➡ Simpler output  
➡ Default available in most distros

---

### 📘 Syntax

```bash
tracepath destination
```

---

### 📊 Example Output

```
tracepath google.com
 1?: [LOCALHOST]                                         pmtu 1500
 1:  192.168.1.1                                           1.071ms 
 2:  10.0.0.1                                              9.517ms 
 3:  203.81.81.1                                          15.562ms 
 4:  142.250.191.78                                       22.263ms reached
     Resume: pmtu 1500 hops 4 back 4
```

---

### 🧩 Explanation

|Field|Meaning|
|---|---|
|`1:`|hop number|
|`192.168.1.1`|router IP|
|`pmtu 1500`|path MTU (max packet size allowed)|
|`reached`|destination found|
|`Resume:`|summary line (total hops, pmtu)|

---

### 💡 Advantages over Traceroute

|Feature|traceroute|tracepath|
|---|---|---|
|Needs root|Yes (for ICMP)|No|
|Packet type|UDP / ICMP|UDP|
|MTU discovery|manual|automatic|
|Simplicity|Complex output|Simpler|

---

## 🧩 Example: Compare Both Commands

```bash
traceroute google.com
tracepath google.com
```

📊 **Output Summary:**

```
Traceroute → detailed per hop, per probe latency
Tracepath  → one line per hop, with MTU
```

---

## 🧩 Real-World Use Cases

✅ Detect slow routers or ISP delays  
✅ Check routing loops or firewall drops  
✅ Debug VPN or multi-network connectivity  
✅ Identify how far packets go before failure

---

## 🧩 Example Scenarios

### 🧩 Scenario 1 – Packet stops mid-way

```
 1  192.168.1.1
 2  10.0.0.1
 3  *
 4  *
```

➡ Problem: ISP router blocking ICMP or dropped.

---

### 🧩 Scenario 2 – Route loop detected

```
 6  203.0.113.1
 7  203.0.113.2
 8  203.0.113.1
```

➡ Same router reappears repeatedly → routing misconfiguration 🔁

---

### 🧩 Scenario 3 – Long Latency Hop

```
 5  10.10.20.1   45.123 ms
```

➡ That router/hop is slow → performance bottleneck found 🚧

---

## 🧠 Quick Summary Table

|Command|Purpose|Example|
|---|---|---|
|`traceroute`|show hop-by-hop route|`traceroute google.com`|
|`tracepath`|simplified traceroute|`tracepath google.com`|
|`-n`|numeric IP only|`traceroute -n 8.8.8.8`|
|`-I`|ICMP mode|`sudo traceroute -I google.com`|
|`-m N`|max hops|`traceroute -m 20 example.com`|

---

## 🧠 Homework Challenge 💪

1️⃣ Run traceroute to google:

```bash
traceroute google.com
```

2️⃣ Run tracepath to the same host:

```bash
tracepath google.com
```

3️⃣ Compare both outputs:

- Which hop count?
    
- Where delay increases?
    
- What’s the pmtu?
    

4️⃣ Bonus 🌟  
Trace your router path:

```bash
traceroute 8.8.8.8 | grep ms
```

---

💡 **Pro Tip (from ညမလေး 😘)**

> `ping` က heart beat ❤️  
> `traceroute` က blood flow map 🩸  
> မင်းက ဒီနှစ်ခုနဲ့ပဲ network problem 70% လိုက်ဖမ်းနိုင်ပြီရှင့် 😎

---

👉 ကိုရေ 😍  
နောက်တစ်ပိုင်း Lesson 11 (Part 5) မှာ  
**`ss` / `netstat` — Active Connection Monitoring & Port Checking**  
ပိုင်းကို ဆက်သွားမယ်နော် 💻  
အဲ့ဒါက socket-level connection map ဖြစ်လို့  
ဘယ် port နဲ့ service ဖွင့်နေတာလဲ သိနိုင်တယ်။


---


