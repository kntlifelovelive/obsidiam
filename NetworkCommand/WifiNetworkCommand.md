

- local wifi network password check 

```bash
sudo grep -r psk= /etc/NetworkManager/system-connections | awk -F'=' '{print $NF}'

```



---

# WiFi CLI Note (Linux)

##  Saved WiFi list (config files)

```bash
sudo ls /etc/NetworkManager/system-connections/
```

- Meaning:

- saved SSID list show 
    

---

# WiFi password extract

```bash
sudo grep -r psk= /etc/NetworkManager/system-connections/
```

- Output:

```
psk=yourpassword
```

-  specific SSID only:

```bash
sudo grep psk= /etc/NetworkManager/system-connections/MyWifi
```

---

#  Scan available WiFi networks

```bash
nmcli device wifi list
```

 show:

- SSID
    
- SIGNAL
    
- SECURITY
    

-  short version:

```bash
nmcli -f IN-USE,SSID,SIGNAL,SECURITY device wifi list
```

---

##  Check network interfaces

```bash
ip a
```

-> wifi interface usually:

- wlan0
    
- wlp2s0
    

---

## Turn WiFi ON / OFF

```bash
nmcli radio wifi on
nmcli radio wifi off
```

---

##  Connect to WiFi (password)

```bash
nmcli device wifi connect "SSID_NAME" password "PASSWORD"
```

-  Example:

```bash
nmcli device wifi connect "MyWifi" password "12345678"
```

---

##  Connect (open WiFi – no password)

```bash
nmcli device wifi connect "SSID_NAME"
```

---

##  Show saved connections

```bash
nmcli connection show
```

---

##  Connect using saved profile

```bash
nmcli connection up "SSID_NAME"
```

---

##  10 Disconnect WiFi

```bash
nmcli connection down "SSID_NAME"
```

---

##  Show current connected WiFi

```bash
nmcli -t -f active,ssid dev wifi | grep yes
```

---

##  Show detailed connection info

```bash
nmcli connection show "SSID_NAME"
```

---

##   Delete saved WiFi

```bash
nmcli connection delete "SSID_NAME"
```

---

#  Advanced (Hacker Style )

##  Monitor mode (need external tools)

```bash
ip link set wlan0 down
iw dev wlan0 set type monitor
ip link set wlan0 up
```

-  used for:

- packet sniffing
    
- wifi analysis
    

---

##  Check signal only

```bash
iw dev wlan0 link
```

---

##  Scan using `iw`

```bash
iw dev wlan0 scan | grep SSID
```

---

#  Important

- `/etc/NetworkManager/system-connections/` → sensitive 
    
- need `sudo`
    
- only use on your own system / lab
    

---

#  Workflow (Real Life)

--> connect WiFi using CLI:

```bash
nmcli device wifi list
nmcli device wifi connect "SSID" password "pass"
```

--> troubleshoot:

```bash
ip a
nmcli device status
ping 8.8.8.8
```

---

#  Summary (One glance)

|Task|Command|
|---|---|
|list saved|`ls /etc/...`|
|scan wifi|`nmcli device wifi list`|
|connect|`nmcli device wifi connect`|
|show current|`nmcli dev wifi`|
|password|`grep psk=`|

---

# Wifi-passCheck

- wifi check command version 1 
- Wifi SSID and Password All 

```bash

sudo grep -r psk= /etc/NetworkManager/system-connections | awk -F':' '{split($1,a,"/"); b=a[length(a)]; gsub(/\.nmconnection$/,"",b); split($2,c,"="); print "📡 " b " → 🔑 " c[2]}'


```

- wifi check command version 3
- Current SSID and Password 

```shell 

sudo grep -rh psk= /etc/NetworkManager/system-connections/ | cut -d= -f2


```