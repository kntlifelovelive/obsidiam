

 **Networking Lesson 11**  _real terminal-level detail_ “ip addr show” output  **deep explanation** 

---

##  Command – `ip addr show`

(Short form 👉 `ip a`)

ဒီ command က Linux system ထဲက **network interfaces** (LAN, Wi-Fi, Loopback, Virtual, etc.)  
အကြောင်းအရာ အကုန်ပြတယ်။

---

### 📘 Syntax

```bash
ip addr show
# or
ip a
```

---

### 📊 Example Output

```bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:9a:bc:ef brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.101/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0
       valid_lft 86400sec preferred_lft 86400sec
    inet6 fe80::a00:27ff:fe9a:bcef/64 scope link 
       valid_lft forever preferred_lft forever
```

---

##  အပိုင်းလိုက်အဓိပ္ပါယ်ရှင်းချက် 👇

---

### 🔹 (1) `1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 ...`

**➡ Interface number:**  
`1:` ဆိုတာ Linux kernel ထဲက interface index number ဖြစ်တယ်။

**➡ Interface name:**  
`lo` = Loopback interface  
➡ Self-communication (127.0.0.1) အတွက် သုံးတယ်။

**➡ Flags (<> ထဲက):**

|Flag|Meaning|
|---|---|
|`UP`|Interface enabled|
|`LOWER_UP`|Physical link is up|
|`BROADCAST`|Supports broadcast|
|`MULTICAST`|Supports multicast traffic|
|`LOOPBACK`|Loopback interface (internal only)|

**➡ `mtu`** (Maximum Transmission Unit):  
Packets တစ်ခုရဲ့ အမြင့်ဆုံး အရွယ်အစား (bytes).  
`65536` for loopback (default).

**➡ `state`**

|Value|Meaning|
|---|---|
|`UP`|active|
|`DOWN`|disabled|
|`UNKNOWN`|loopback or virtual|

**➡ `qdisc`** (Queue discipline):  
Packet scheduling method, e.g., `fq_codel`, `noqueue`.

---

### 🔹 (2) `link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00`

**➡ link type:** loopback / ether / tunnel

- `loopback` → internal device
    
- `ether` → Ethernet interface (has MAC address)
    

**➡ MAC Address:**  
`00:00:00:00:00:00` → loopback has no real MAC.

**➡ brd:**  
Broadcast address — for Ethernet, usually `ff:ff:ff:ff:ff:ff`.

---

### 🔹 (3) `inet 127.0.0.1/8 scope host lo`

**➡ inet:** IPv4 address assigned to interface  
**➡ 127.0.0.1/8** → loopback range  
**➡ scope host** → can be used only by this machine  
**➡ `lo`** → interface name

**➡ `valid_lft` / `preferred_lft`:**  
Lifetime (for dynamic addresses)

- `forever` → static IP
    
- `86400sec` → dynamic (DHCP assigned)
    

---

### 🔹 (4) `inet6 ::1/128 scope host`

IPv6 version of loopback address  
➡ Equivalent to IPv4 127.0.0.1

---

### 🔹 (5) `2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> ...`

`eth0` = Ethernet interface  
Real network card / virtual bridge.

**➡ mtu 1500:** default for Ethernet networks (standard packet size)

---

### 🔹 (6) `link/ether 08:00:27:9a:bc:ef brd ff:ff:ff:ff:ff:ff`

**➡ link/ether:** physical layer device type (Ethernet)  
**➡ 08:00:27:9a:bc:ef:** MAC Address (hardware address)

💡 MAC Address unique to your NIC (Network Interface Card)

---

### 🔹 (7) `inet 192.168.1.101/24 brd 192.168.1.255 scope global dynamic ...`

|Field|Meaning|
|---|---|
|`192.168.1.101/24`|IPv4 address & subnet mask|
|`/24`|CIDR notation (255.255.255.0)|
|`brd 192.168.1.255`|broadcast address|
|`scope global`|can communicate with other networks|
|`dynamic`|assigned by DHCP|
|`noprefixroute`|manual route not created|

**➡ valid_lft / preferred_lft:**  
Time (in seconds) until DHCP lease expires.

---

### 🔹 (8) `inet6 fe80::a00:27ff:fe9a:bcef/64 scope link`

➡ IPv6 auto-generated “link-local” address  
➡ Works only within local LAN  
➡ Each device gets one automatically.

---

## 💡 Quick Summary Table

|Field|Description|Example|
|---|---|---|
|Interface|Device name|`eth0`, `wlan0`, `lo`|
|State|Status|`UP`, `DOWN`, `UNKNOWN`|
|Flags|Capabilities|`BROADCAST`, `MULTICAST`|
|MTU|Max packet size|`1500`|
|MAC|Hardware address|`08:00:27:xx:yy:zz`|
|inet|IPv4 address|`192.168.1.101/24`|
|inet6|IPv6 address|`fe80::abcd::1234/64`|
|scope|Visibility|`host`, `link`, `global`|
|valid_lft|Lease time|`86400sec` or `forever`|

---

## 🧠 Example: Read the Output Like a Pro

```
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    link/ether 80:be:05:22:19:4a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.104/24 brd 192.168.0.255 scope global dynamic wlan0
       valid_lft 7182sec preferred_lft 7182sec
```

**Interpretation:**

- Interface #2 = `wlan0` (Wi-Fi)
    
- Device is active (`UP`)
    
- MAC = 80:be:05:22:19:4a
    
- IP = 192.168.0.104/24
    
- Router broadcast = 192.168.0.255
    
- Address assigned by DHCP
    
- Lease valid for ~2 hours (7182 sec)
    

---

💡 **Pro Tip (from ညမလေး 😘)**

> “ip addr show” ကို နားလည်တာနဲ့ network troubleshooting 50% ပြီးသွားတယ်။  
> ဘယ် IP assign ဖြစ်တယ်၊ interface up/down ဖြစ်လား၊  
> MAC address, DHCP, IPv6, broadcast—all visible in one glance 💪

---
အိုဟ့် 🥰 တော်တယ် ကိုရေ —  
အခုတော့ Networking lesson 11 ရဲ့ **part 2** — `ip link` နဲ့ `ip route` ကို  
အနည်းဆုံး network engineer level နဲ့ ပြောပြမယ်နော် 💪

---

# 🌐 Lesson 11 – Part 2

## 🧩 `ip link` & `ip route` (Mastery Level Explanation)

---

## 🔹 1️⃣ `ip link` — Interface Hardware Layer Info

`ip link` က network interface (hardware-level) စနစ်ကို ပြသပေးတဲ့ command ပါ။  
`ip addr` ကတော့ IP info (Layer 3) ပဲ။  
ဒါပေမဲ့ `ip link` ကတော့ Layer 2 level (MAC, MTU, state) အထိပြတယ်။

---

### 📘 Syntax

```bash
ip link show
# or short form
ip l
```

---

### 📊 Example Output

```bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:bc:8a:ef brd ff:ff:ff:ff:ff:ff
```

---

### 🧠 Breakdown & Explanation

|Field|Description|Example|
|---|---|---|
|`1:`|Interface index|`1` (lo), `2` (eth0)|
|`lo:`|Interface name|loopback|
|`<LOOPBACK,UP,LOWER_UP>`|Flags|Interface status|
|`mtu`|Max Transmission Unit|bytes per packet|
|`qdisc`|Queue discipline|`noqueue`, `fq_codel`|
|`state`|Interface state|`UP`, `DOWN`, `UNKNOWN`|
|`mode`|Interface mode|`DEFAULT`, `DORMANT`|
|`link/ether`|Link type (Ethernet)|hardware layer|
|`08:00:27:bc:8a:ef`|MAC address|unique per NIC|
|`brd`|Broadcast MAC|`ff:ff:ff:ff:ff:ff`|
|`qlen`|Transmit queue length|number of packets buffer|

---

### 🧩 Interface Control Examples

**Bring interface up:**

```bash
sudo ip link set eth0 up
```

**Bring interface down:**

```bash
sudo ip link set eth0 down
```

**Change MTU (packet size):**

```bash
sudo ip link set eth0 mtu 1400
```

**Rename interface:**

```bash
sudo ip link set eth0 name lan0
```

**Show only active links:**

```bash
ip -br link show up
```

➡ `-br` = brief format (compact)

**Example Output:**

```
lo      UNKNOWN 127.0.0.1
eth0    UP       192.168.1.10
wlan0   UP       192.168.1.12
```

---

### 💡 Summary

- `ip link` → Layer 2 info (MAC, state)
    
- `ip addr` → Layer 3 info (IP, subnet)
    
- Both are part of `ip` utility suite (`iproute2` package).
    

---

## 🔹 2️⃣ `ip route` — Routing Table Management

`ip route` ကတော့ Linux Kernel ရဲ့ Routing Table ကို ပြတယ်။  
ဟုတ်ပါတယ် 😎 “packet တစ်ခု ဘယ်လိုနေရာအရောက်ရမလဲ” ဆိုတာ kernel ရဲ့ “map” ဖြစ်တယ်။

---

### 📘 Syntax

```bash
ip route show
# or short form
ip r
```

---

### 📊 Example Output

```
default via 192.168.1.1 dev eth0 proto dhcp metric 100
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.101 metric 100
```

---

### 🧠 Breakdown & Explanation

#### 🧩 1️⃣ `default via 192.168.1.1 dev eth0`

|Field|Meaning|
|---|---|
|`default`|All other traffic (no specific route)|
|`via 192.168.1.1`|Next-hop (gateway IP)|
|`dev eth0`|Interface used to reach gateway|
|`proto dhcp`|Added by DHCP client|
|`metric 100`|Route priority (lower = preferred)|

➡ _Summary:_  
Packets to unknown networks go through the router 192.168.1.1 using eth0.

---

#### 🧩 2️⃣ `192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.101`

|Field|Meaning|
|---|---|
|`192.168.1.0/24`|Local network subnet|
|`dev eth0`|Interface used|
|`proto kernel`|Added automatically|
|`scope link`|Valid only in local network|
|`src 192.168.1.101`|Source IP for packets|
|`metric 100`|Priority value|

➡ _Summary:_  
Packets going to local subnet (192.168.1.x) go directly through eth0.

---

### 🧩 Example Diagram

```
[Linux Host: 192.168.1.101] 
       |
       | (eth0)
       |
[Router: 192.168.1.1] ---- Internet 🌍
```

💬 Route table ဆိုတာက ဒီ map ကို Linux kernel မှာ တင်ထားတာပါ။

---

### 🧩 Adding / Removing Routes

**Add static route:**

```bash
sudo ip route add 10.0.0.0/24 via 192.168.1.1
```

➡ Any packet to 10.0.0.0/24 → goes via 192.168.1.1

**Add route via another interface:**

```bash
sudo ip route add 172.16.0.0/16 dev wlan0
```

**Delete route:**

```bash
sudo ip route del 10.0.0.0/24
```

**Replace (update):**

```bash
sudo ip route replace default via 192.168.1.254
```

**Flush all routes (⚠ dangerous):**

```bash
sudo ip route flush all
```

---

### 🧩 Example: Multi-Network Host

|Destination|Gateway|Interface|
|---|---|---|
|192.168.1.0/24|—|eth0|
|10.10.0.0/24|192.168.1.5|eth0|
|default|192.168.1.1|eth0|

➡ ပုံမှန် traffic → internet via default  
➡ Internal lab traffic → 10.10.0.0 via 192.168.1.5

---

### 🧩 Show route to specific host

```bash
ip route get 8.8.8.8
```

**Output Example:**

```
8.8.8.8 via 192.168.1.1 dev eth0 src 192.168.1.101
```

➡ This tells you which interface and gateway will be used to reach Google DNS.

---

### 🧩 Default Route Concept Diagram

```
             ┌──────────────┐
             │  Internet 🌍 │
             └──────┬───────┘
                    │
         via 192.168.1.1 (Router)
                    │
         ┌──────────┴──────────┐
         │   Linux System      │
         │   IP: 192.168.1.101 │
         └─────────────────────┘
```

💡 Default route = Gateway that handles “everything else.”

---

## 🧠 Comparison Table

|Command|Focus|Example|Description|
|---|---|---|---|
|`ip link`|Interface physical layer|`ip link show`|Show MAC, MTU, flags|
|`ip addr`|Interface network layer|`ip addr show`|Show IP addresses|
|`ip route`|Routing layer|`ip route show`|Show routing table|

---

## 🧩 Homework Challenge 😎

1️⃣ Interface info check

```bash
ip link show
```

➡ Identify your active interfaces and MAC addresses.

2️⃣ Bring interface down & up

```bash
sudo ip link set wlan0 down
sudo ip link set wlan0 up
```

3️⃣ Show routing table

```bash
ip route
```

4️⃣ Add your own test route

```bash
sudo ip route add 192.168.55.0/24 via 192.168.1.1
```

5️⃣ Verify path

```bash
ip route get 192.168.55.1
```

---

💡 **Pro Tip (from ညမလေး 😘)**

> Network troubleshooting မှာ “ip link” နဲ့ “ip route” တို့ကို နားလည်တာ  
> ဘယ် Wi-Fi, Ethernet, VPN, container network သုံးနေသလဲ ဆိုတာ သိသွားတယ်။  
> မင်းက Kernel networking map ကို သေချာဖတ်တတ်လာတာနဲ့ 💪  
> Routing loop, gateway loss, or dual-interface conflict တွေကို စစ်သိနိုင်ပြီရှင့် 😍

---

ကိုရေ 😘  
နောက်တစ်ပိုင်းမှာ “**ping**, **traceroute**, **ss**, **netstat**, **dig**, **nc**”  
တွေကို ထပ်ပြီး _packet-level_ explanation နဲ့ example တင်ပေးမယ်။

မင်းက ဆက်သွားချင်တာ ဘယ် command ဖြစ်လဲ?  
`ping` ပိုင်းကို စတင်သွားမလားရှင့် 😄?