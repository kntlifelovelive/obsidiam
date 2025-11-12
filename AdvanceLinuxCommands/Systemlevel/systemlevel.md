

---

##  **Linux File System Structure**

Linux မှာ root directory (`/`) က base ဖြစ်ပြီး  
အဲ့ထဲမှာ subdirectories တွေရှိပါတယ်။  
တစ်ခုချင်းစီက OS ရဲ့ function တစ်ခုကိုကိုယ်စားပြုပါတယ်။

File system tree ကို ပုံဖော်ပြရရင် 👇

```
/
├── bin/
├── boot/
├── dev/
├── etc/
├── home/
├── lib/
├── media/
├── mnt/
├── opt/
├── root/
├── sbin/
├── tmp/
├── usr/
└── var/
```

---

## **1. /etc – System Configuration Files**

– Linux system ရဲ့ setting files တွေ အကုန်ရှိတဲ့နေရာ။  
System-wide configuration files, service setup, network setting တို့ကို သိမ်းထားပါတယ်။

**Example Files:**

- `/etc/passwd` → user accounts list
- `/etc/hosts` → local hostname mapping
- `/etc/fstab` → file system mount information
- `/etc/ssh/sshd_config` → SSH server configuration

**Practice:**

```bash
ls /etc
cat /etc/hostname
cat /etc/passwd | head
```

**အကြောင်းရှင်းချက်:**  
SSH service ကို configure လုပ်ချင်ရင် `/etc/ssh/sshd_config` ကို edit လုပ်ရပါတယ်။  

```bash
sudo nano /etc/ssh/sshd_config
# Port 22 ကို Port 2222 ပြောင်းနိုင်တယ်
```

---

##  **2. /home – User Home Directories**

– အသုံးပြုသူတိုင်းအတွက် personal folder ပါ။  
**User data, documents, downloads** စတာတွေကို သိမ်းတာဖြစ်ပါတယ်။

**Example:**

- `/home/kyaw/Downloads`
- `/home/kyaw/Desktop`
- `/home/love/Documents`


**Practice:**

```bash
ls /home
cd ~
pwd
```

---

##  **3. /var – Variable Files**

 – “Variable data” ဆိုတဲ့အတိုင်း ပြောင်းလဲနေတဲ့ data တွေရှိရာနေရာ။  
ဥပမာ log files, cache files, mail queues, spool data, temporary storage စတာတွေပါ။

**Example:**

- `/var/log/syslog` → system log
- `/var/cache/apt/` → apt cache
- `/var/spool/mail` → mail queue

**Practice:**

```bash
ls /var/log
sudo tail -n 10 /var/log/syslog
```

 **အကြောင်းရှင်းချက်:**  
System မှာ event ဖြစ်တိုင်း `/var/log` ထဲမှာ record လုပ်တာပါ။  
ဥပမာ: Error ဖြစ်သွားရင် logs ထဲကနေ trace လုပ်နိုင်ပါတယ်။

---

##  **4. /usr – User Binaries & Read-only Data**

– user-level programs (binaries), libraries, docs တွေရှိရာနေရာ။  
**System-wide apps** တွေကို `/usr/bin` မှာထည့်ထားတတ်ပါတယ်။

**Example:**

- `/usr/bin` → Commands (e.g., `python`, `vim`, `gcc`)
- `/usr/share` → Shared data (e.g., wallpapers, icons)
- `/usr/lib` → Libraries (.so files)

**Practice:**

```bash
ls /usr/bin | head
which python3
ls /usr/share/icons
```

**အကြောင်းရှင်းချက်:**  
 `python3` ကို run လိုက်ရင် `/usr/bin/python3` ကနေ program run ဖြစ်တယ်။  
အဲ့တာက system-wide installation ဖြစ်တာ။

---

##  **5. /bin – Essential User Binaries**

– OS boot တုန်းကပင်လိုအပ်တဲ့ “အခြေခံ command binaries” တွေ။  
ဥပမာ system boot လုပ်သွားဖို့အတွက်လို commands တွေ။

**Example Commands:**

- `/bin/ls`
- `/bin/cp`
- `/bin/mv`
- `/bin/bash`

**Practice:**

```bash
ls /bin | grep bash
file /bin/ls
```

 **အကြောင်းရှင်းချက်:**  
`/bin` ထဲက commands တွေက emergency mode (rescue shell) မှာတောင် လုပ်နိုင်ပါတယ်။

---

##  **6. /tmp – Temporary Files**

– temporary files တွေရှိတဲ့နေရာ။  
Program တွေ run တုန်းမှာ cache / session data သိမ်းဖို့ သုံးတယ်။  
System reboot အပြီးမှာ /tmp ထဲက file တွေကို Linux auto-delete လုပ်တတ်တယ်။

**Example:**

- `/tmp/testfile.txt`
- `/tmp/systemd-private-xxxx`

**Practice:**

```bash
cd /tmp
touch hello.txt
ls -l
```

🧩 **အကြောင်းရှင်းချက်:**  
သင် script တစ်ခု run တုန်းမှာ output သိုလှောင်ချင်တာရှိရင် /tmp ထဲသုံးနိုင်တယ်။  
ဥပမာ:

```bash
echo "temporary data" > /tmp/temp.txt
cat /tmp/temp.txt
```

---

## 🔍 **Summary Table**

|Directory|Description|Example|
|---|---|---|
|`/etc`|System configuration files|`/etc/hosts`, `/etc/passwd`|
|`/home`|User home directories|`/home/kyaw/Downloads`|
|`/var`|Variable data like logs, cache|`/var/log/syslog`|
|`/usr`|User-level programs|`/usr/bin/python3`|
|`/bin`|Essential commands|`/bin/ls`, `/bin/bash`|
|`/tmp`|Temporary files|`/tmp/temp.txt`|

---

## 💡 **Practice Challenge for You 😎**

👉 လေ့ကျင့်ဖို့ command ၃ ခုပေးမယ်။  
လုပ်ပြီး Output Screenshot ပြသုံးပါ (မင်း Linux machine မှာ run လုပ်ဖို့นะ 😁)

1️⃣ `/etc` ထဲက `.conf` file တွေကို ရှာပါ

```bash
find /etc -name "*.conf" | head
```

2️⃣ ကိုယ့် username ရဲ့ home directory ထဲမှာ ဘာရှိတယ်ဆိုတာပြပါ

```bash
ls -lah ~
```

3️⃣ `/var/log` ထဲက 10 latest log file name တွေကိုပြပါ

```bash
ls -lt /var/log | head
```

---

ညမလေးပြောချင်တာတစ်ချက်ရှိတယ်နော် 💕  
ဒီ folder structure ကို သေချာနားလည်ပြီးမှ စနစ်တကျ system ကို control လုပ်နိုင်တာပါ။  
ဒီအဆင့်ကိုသေချာလေ့ကျင့်နိုင်ရင် **Linux master path** အဖို့ တကယ်ကောင်းတဲ့ foundation ဖြစ်သွားပါမယ်ရှင့် 💪

---

လိုချင်လား ကိုကျော်ရေ 😍 —  
ဒီ Step 1 အပြီး အခု **Step 2 (System Management – processes, disks, services)** ကို  
နောက်တစ်ဆင့်သွားဖို့ guide line ပေးလိုက်ပါဦးလား?