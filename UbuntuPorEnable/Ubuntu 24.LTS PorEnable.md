Ubuntu Pro ကို setup လုပ်ရန်အတွက် အောက်ပါအဆင့်ဆင့်ကို လိုက်နာနိုင်ပါတယ်။ Ubuntu Pro သည် အရင်က Ubuntu Advantage လို့ခေါ်ခဲ့ပြီး Ubuntu သုံးသူများအတွက် အထူးပံ့ပိုးမှုများ (Support and Security Patches) ပေးစွမ်းသည်။

### 1. **Ubuntu Pro Account ရယူရန်**
Ubuntu Pro သုံးရန် Canonical Account လိုအပ်ပါတယ်။
- [Canonical Sign Up](https://login.ubuntu.com/) သို့သွားပြီး Account တစ်ခု ဖန်တီးပါ။
- အကောင့်ရှိပြီးသားဖြစ်ရင် login ဝင်ပါ။

---

### 2. **Ubuntu Pro Subscription Key ရယူရန်**
Canonical မှ Ubuntu Pro subscription key ကို ရယူပါ။
- [Ubuntu Pro Page](https://ubuntu.com/pro) သို့သွားပါ။
- "Get a free personal subscription" လင့်ခ်ကိုနှိပ်ပြီး သင့်အကောင့်နဲ့ ပြုလုပ်ပါ။

---

### 3. **Ubuntu Pro Enable လုပ်ရန်**
Terminal ကိုဖွင့်ပြီး အောက်ပါအဆင့်များကို လိုက်နာပါ။

1. **Ubuntu Pro CLI Install လုပ်ရန်**
   ```bash
   sudo apt update
   sudo apt install ubuntu-advantage-tools
   ```

2. **Ubuntu Pro Attach လုပ်ရန်**
   Subscription Key ကို သင့်အကောင့်မှ ရယူပြီး attach လုပ်ပါ။
   ```bash
   sudo pro attach <your_subscription_key>
   ```

3. **Enable Livepatch (Optional)**
   Livepatch သည် Kernel Updates မပြုလုပ်ဘဲ ရှိသမျှ updates ကို လုပ်ပေးနိုင်စေပါသည်။
   ```bash
   sudo pro enable livepatch
   ```

---

### 4. **Ubuntu Pro Features အသုံးပြုရန်**
Ubuntu Pro သည် အောက်ပါများအတွက် အသုံးဝင်သည်:
- Expanded Security Maintenance (ESM)
- FIPS-certified cryptographic modules
- Compliance management tools
- Livepatch (Kernel updates without rebooting)

**Example: ESM Enable**
```bash
sudo pro enable esm-apps
sudo pro enable esm-infra
```

---

### 5. **Ubuntu Pro Status Check**
Ubuntu Pro အခြေအနေကို စစ်ဆေးရန်:
```bash
sudo pro status
```

---
## note 

Ubuntu os ကို Pro-Enable key အသုံးပြုထားတယ်ဆိုပါက Ubuntu Os အသစ်ပြန်မတင်ခင် pro-api-key ကို ဖြုတ်လိုက်သင့်ပါသည်။ 

**commands line enable key setup:**
```
sudo pro detach

```

---
---


## My Ubuntu Pro Account - API

```bash

sudo pro attach C1Xpk9qbMMHN1m6cxPJyi5qumUrJB


```


```bash 
SERVICE          ENTITLED  STATUS       DESCRIPTION
anbox-cloud      yes       disabled     Scalable Android in the cloud
cc-eal           yes       n/a          Common Criteria EAL2 Provisioning Packages
esm-apps         yes       enabled      Expanded Security Maintenance for Applications
esm-infra        yes       enabled      Expanded Security Maintenance for Infrastructure
fips             yes       n/a          NIST-certified FIPS crypto packages
fips-preview     yes       n/a          Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     yes       n/a          FIPS compliant crypto packages with stable security updates
landscape        yes       disabled     Management and administration tool for Ubuntu
livepatch        yes       enabled      Canonical Livepatch service
realtime-kernel  yes       disabled     Ubuntu kernel with PREEMPT_RT patches integrated
├ generic        yes       disabled     Generic version of the RT kernel (default)
├ intel-iotg     yes       n/a          RT kernel optimized for Intel IOTG platform
└ raspi          yes       n/a          24.04 Real-time kernel optimised for Raspberry Pi
ros              yes       n/a          Security Updates for the Robot Operating System
ros-updates      yes       n/a          All Updates for the Robot Operating System
usg              yes       n/a          Security compliance and audit tools

Enable services with: pro enable <service>

     Account: kyawnyeinthant9@gmail.com
Subscription: Ubuntu Pro - free personal subscription
```

---

