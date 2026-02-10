
---

## Network Manager ရှိ/မရှိ စစ်မယ်

```bash
systemctl status NetworkManager
```

မ run သေးရင်

```bash
sudo systemctl enable --now NetworkManager
```

---

##  Wi-Fi scan (CLI)

####  Wi-Fi device 

```bash
nmcli device
```

`wlan0` / `wlp…` လိုမျိုး တွေ့ရပါမယ်

---

###  Network scan

```bash
nmcli device wifi list
```

 SSID, SIGNAL, SECURITY အကုန်မြင်ရမယ်

---

##  Wi-Fi connect (password ပါ)

```bash
nmcli device wifi connect "SSID_NAME" password "PASSWORD"
```

ဥပမာ

```bash
nmcli device wifi connect "MyWifi" password "12345678"
```

 connect ဖြစ်ရင် auto save ဖြစ်သွားပါတယ်

---

##  Open Wi-Fi (password မလို)

```bash
nmcli device wifi connect "FreeWifi"
```

---

##  Wi-Fi reconnect

```bash
nmcli connection up "MyWifi"
```

---

##  Disconnect

```bash
nmcli device disconnect wlan0
```

---

##  Saved Wi-Fi list

```bash
nmcli connection show
```

Delete ချင်ရင်

```bash
nmcli connection delete "MyWifi"
```

---

##  shortcut (scan + connect)

```bash
nmcli d wifi l
nmcli d wifi c "SSID" password "PASS"
```

---



