
# GPG Support လုပ်သော Digest Algorithms နှင့် အသုံးပြုနည်းများ

GPG မှာ **Digest Algorithms** တွေကို hashing အတွက် သုံးပြီး, အလုံခြုံဆုံးနဲ့ အမြန်ဆုံး hashing algorithm ကို သင့်လုပ်ဆောင်မှုအလိုက် ရွေးချယ်အသုံးပြုနိုင်ပါတယ်။ 

---

## **GPG Support လုပ်သော Digest Algorithms Table**  

| **Algorithm** | **Hash Length** | **Security Level**        | **Performance** | **Current Status**        | **Notes**                                    |
|----------------|-----------------|---------------------------|-----------------|----------------------------|---------------------------------------------|
| **MD5**        | 128-bit         | Weak (Collision Found)    | Fast            | Deprecated                 | မသုံးသင့်ပါ (SHA အမျိုးအစားတွေသုံးပါ)      |
| **SHA1**       | 160-bit         | Weak (Collision Found)    | Moderate        | Outdated                   | Legacy systems များအတွက်သာ သုံးပါ။         |
| **SHA224**     | 224-bit         | Moderate                  | Fast            | Supported                  | SHA256 ထက် security နည်းပါတယ်။             |
| **SHA256**     | 256-bit         | Strong                    | Fast            | Recommended for normal use | Default အဖြစ် GPG မှာ သုံးပါတယ်။            |
| **SHA384**     | 384-bit         | Very Strong               | Slower          | Supported                  | လုံခြုံမှုပိုလိုတဲ့နေရာတွင် သင့်တော်။       |
| **SHA512**     | 512-bit         | Very Strong               | Slowest         | Recommended for high security | အမြင့်ဆုံး security လိုအပ်တဲ့နေရာတွင် သင့်တော်။ |

---

## **Performance Order (မြန်ဆန်မှုအလိုက်)**  
MD5 > SHA1 > SHA224 > SHA256 > SHA384 > SHA512  

---

### **GPG Command Example များ**
#### **1. Symmetric Encryption with SHA512**

**Command**  

```bash
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA512 file.zip
```  

**Description**  

- **`--digest-algo SHA512`**: File hashing အတွက် `SHA512` သုံးပြီး အလွန်လုံခြုံတဲ့ encryption ကိုလုပ်ဆောင်ပေးပါတယ်။  
- **`--passphrase-file passwd.txt`**: Password ကို `passwd.txt` ဖိုင်ထဲမှတဆင့် ထည့်သွင်းပြီး automation လုပ်နိုင်သည်။  

---

### **2. Time Command Usage**  
**Command**  
```bash
time gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA256 file.zip
```  
**Description**  
- **`time`**: Encryption process ကြာချိန်ကို တိုင်းတာဖော်ပြသည်။  
- Output:
  - **real**: Command run ခဲ့တဲ့ အချိန်အားလုံး။
  - **user**: CPU ကို actual hash computation အတွက် အသုံးပြုတဲ့အချိန်။
  - **sys**: File read/write နှင့် kernel-level I/O operation အတွက် လိုအပ်တဲ့အချိန်။  


**Example Output**  

```plaintext
real    0m3.512s
user    0m2.850s
sys     0m0.150s
```

---

### **3. Overwrite Prevention**
**Command**  
```bash
gpg --batch --passphrase-file passwd.txt --symmetric file.zip
```  
**Description**  
- **`--yes` flag** မထည့်ပါက ဖိုင်ရှိပြီးသားနေရာတွင် overwrite မဖြစ်စေဘဲ အတည်ပြုမှုကို မေးမြန်းလိမ့်မည်။

---

#### **4. Multiple Algorithms Test**  
**Command**  
```bash
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA256 file.zip
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA512 file.zip
```  
**Description**  
- တူညီသောဖိုင်ကို `SHA256` နှင့် `SHA512` အလိုက် hashing လုပ်ပြီး အမြန်နှုန်း (Performance) နှင့် security ကို ယှဉ်ပြနိုင်သည်။

---

#### **Recommendation**  
1. **General Use:**  
   - **SHA256** သည် default hashing အဖြစ်လုံခြုံပြီး မြန်ဆန်ပါတယ်။
2. **High-Security Needs:**  
   - **SHA512** သည် အလွန်လုံခြုံသော hashing အတွက် အသင့်တော်ဆုံးဖြစ်သည်။  
   - Sensitive data သို့မဟုတ် Critical Encryption အတွက် သုံးပါ။

---

### **မှတ်ချက်**  
1. GPG သည် default digest-algo အဖြစ် **SHA256** သုံးသည်။  
2. Digest-algo သည် **File Encryption** ကိုမထိခိုက်ဘဲ hashing process ကိုသာသက်ဆိုင်သည်။  
3. **Time Command** သုံးပြီး Performance တွေကို ကြည့်ပြီး optimization ပြုလုပ်နိုင်သည်။

--- 

**သုံးစွဲနည်း** :: အထက်ပါနမူနာများကို ကိုယ့်ရဲ့အလုပ်လိုအပ်ချက်နှင့် security level အလိုက် စမ်းသုံးနိုင်ပါပြီ။ 



---


# **GPG Algorithm အသုံးပြုပုံ နမူနာများ (Digest Algorithm)**  

#### **Command: SHA256**
```bash
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA256 file.zip
```
**Description**  
- `SHA256` သည် default algorithm ဖြစ်ပြီး လုံခြုံမှုနှင့် မြန်နှုန်းအပေါ် အလယ်အလတ် သင့်တော်သည်။  
- Password ကို `passwd.txt` ဖိုင်မှ တဆင့် ထည့်သွင်းပြီး symmetric encryption လုပ်သည်။  

---

#### **Command: SHA512**
```bash
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA512 file.zip
```
**Description**  
- `SHA512` သည် file hashing အတွက် အလွန်လုံခြုံသော algorithm ဖြစ်သည်။  
- အမြင့်ဆုံး security လိုအပ်သော data encryption များအတွက် သင့်တော်သည်။

---

#### **Command: SHA1**
```bash
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA1 file.zip
```
**Description**  
- `SHA1` သည် ယခင်တွင် နာမည်ကျော်သော်လည်း security တိုးတက်မှုများကြောင့် လက်ရှိမှာ အားနည်းနေပြီဖြစ်သည်။  
- Legacy system သို့မဟုတ် backward compatibility လိုအပ်သော data encryption အတွက်သာ သုံးသင့်သည်။

---

#### **Command: MD5**
```bash
gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo MD5 file.zip
```
**Description**  
- `MD5` သည် အလွန်မြန်ဆန်သော်လည်း security အတွက် အားနည်းပြီး collision ဖြစ်နိုင်မှုများသောကြောင့် အကြံမပြုပါ။  

---

### **Performance and Security Testing (ယှဉ်ပြရန်)**  
အနားမှာ **`time`** ကို ထည့်ပြီး process ကြာချိန်ကို တိုင်းတာနိုင်သည်။  

#### **Example (SHA256 vs SHA512):**
```bash
time gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA256 file.zip
time gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA512 file.zip
```

#### **Sample Output:**
```plaintext
# SHA256
real    0m1.210s
user    0m1.050s
sys     0m0.030s

# SHA512
real    0m1.450s
user    0m1.300s
sys     0m0.040s
```
**Note:** SHA512 သည် SHA256 ထက် processing အချိန်ပိုယူသော်လည်း security ပိုမိုတိုးတက်သည်။  

---

### **လုံခြုံရေးအတွက် အကြံပြုချက်များ**  
1. **အမြင့်ဆုံး security:** `SHA512` သုံးပါ။  
2. **မြန်နှုန်းနှင့် လုံခြုံရေးအလယ်အလတ်:** `SHA256` သုံးပါ။  
3. **Legacy System**: Compatibility လိုအပ်ပါက `SHA1` သုံးပါ။  
4. **MD5:** အမြန်နှုန်းလိုအပ်သော်လည်း security မလိုအပ်သော temporary data အတွက်သာ သုံးပါ။  

---  
---

# **GPG Command Options နမူနာများနှင့် အဓိပ္ပါယ်**  

#### **1. `--batch`**
- **Function:**  
  - Automation script တွေမှာ interactive prompt မတက်စေဘဲ CLI command ကနေ အလိုအလျောက် run ဖို့ သုံးတယ်။
- **Use Case:**  
  - User interaction မလိုအပ်ဘဲ automated system တွေမှာ GPG သုံးချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --batch --symmetric --passphrase "mypassword" file.zip
  ```

---

#### **2. `--yes`**
- **Function:**  
  - File overwrite prompts (e.g., existing .gpg files) ကို အလိုအလျောက် `Yes` ဆိုပြီး လက်ခံဖို့ သုံးတယ်။
- **Use Case:**  
  - Same filename နဲ့ encrypted file ကို overwrite လုပ်ဖို့ လိုချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --yes --symmetric --passphrase "mypassword" file.zip
  ```

---

#### **3. `--symmetric`**
- **Function:**  
  - Symmetric encryption လုပ်ပြီး Password သာ အသုံးပြုကာ Encrypt/Decrypt လုပ်ဖို့ သုံးတယ်။
- **Use Case:**  
  - လက်ခံသူအနေနဲ့ password သာလောက်ပြီး ပြန်ဖွင့်နိုင်ဖို့။
- **Example:**  
  ```bash
  gpg --symmetric --passphrase "mypassword" file.zip
  ```

---

#### **4. `--passphrase-file`**
- **Function:**  
  - Password ကို ဖိုင်ထဲကနေတဆင့် သုံးဖို့ ရည်ရွယ်တယ်။
- **Use Case:**  
  - Script တွေမှာ Password ကို ဖိုင်ထဲ ထားပြီး CLI command မှာ direct ထည့်ရတာ ရှောင်ကြဉ်ဖို့။
- **Example:**  
  ```bash
  gpg --passphrase-file passwd.txt --symmetric file.zip
  ```

---

#### **5. `--digest-algo`**
- **Function:**  
  - Hash algorithm (e.g., SHA256, SHA512) သတ်မှတ်ဖို့ သုံးတယ်။
- **Use Case:**  
  - Security level အနက် hashing algorithm ကို control လုပ်ချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --digest-algo SHA512 --symmetric file.zip
  ```

---

#### **6. `--cipher-algo`**
- **Function:**  
  - Encryption algorithm (e.g., AES256, AES192, AES128) သတ်မှတ်ဖို့ သုံးတယ်။
- **Use Case:**  
  - File encryption ကို လုံခြုံမှုအဆင့်အလိုက် ညှိချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --cipher-algo AES256 --symmetric file.zip
  ```

---

#### **7. `--armor`**
- **Function:**  
  - ASCII-armored output ပြောင်းဖို့ သုံးတယ်။ (e.g., Binary data ကို text format ပြောင်းပြီး ပို့ရန်သင့်တော်)
- **Use Case:**  
  - Email သို့မဟုတ် text-based transmission systems တွေမှာ ပို့ဖို့။
- **Example:**  
  ```bash
  gpg --armor --symmetric --passphrase "mypassword" file.zip
  ```

---

#### **8. `--output`**
- **Function:**  
  - Output file name ကိုသတ်မှတ်ဖို့ သုံးတယ်။
- **Use Case:**  
  - Output file ကို သတ်မှတ်ချက်မရမီ default လှမ်းထားသော filename မလွှဲချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --symmetric --passphrase "mypassword" --output encrypted_file.gpg file.zip
  ```

---

#### **9. `--compress-algo`**
- **Function:**  
  - Compression algorithm (e.g., ZLIB, BZIP2) ကို control လုပ်ဖို့ သုံးတယ်။
- **Use Case:**  
  - File size ကို small ဖို့အတွက် compression algorithm သုံးချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --compress-algo ZLIB --symmetric file.zip
  ```

---

#### **10. `--decrypt`**
- **Function:**  
  - Encrypted file ကို password သို့မဟုတ် private key အကူအညီနဲ့ ပြန်ဖွင့်ဖို့။
- **Use Case:**  
  - Encrypted .gpg file တစ်ခုကို original file ပြန်ယူဖို့။
- **Example:**  
  ```bash
  gpg --decrypt --passphrase "mypassword" file.zip.gpg
  ```

---

#### **11. `--recipient`**
- **Function:**  
  - Public Key ကို သတ်မှတ်ပြီး recipient-specific encryption လုပ်ဖို့။
- **Use Case:**  
  - Encrypted file ကို သတ်မှတ်ထားသော recipient Public Key နဲ့သာ ဖွင့်နိုင်ရန်။
- **Example:**  
  ```bash
  gpg --encrypt --recipient user@example.com file.zip
  ```

---

#### **12. `--trust-model`**
- **Function:**  
  - Key trust level ကို override လုပ်ပြီး manual control ပေးဖို့။
- **Use Case:**  
  - Key trust checking process ကို skip လုပ်ချင်တဲ့အခါ။
- **Example:**  
  ```bash
  gpg --trust-model always --encrypt --recipient user@example.com file.zip
  ```

---

### **Example Commands Combined**
1. **Encrypt (High Security):**
   ```bash
   gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA512 --cipher-algo AES256 --output secure_file.gpg file.zip
   ```

2. **Decrypt:**
   ```bash
   gpg --batch --yes --passphrase-file passwd.txt --decrypt secure_file.gpg
   ```

---

### **Tips:**
- **Automation:** Use `--batch` and `--yes` for non-interactive scripting.  
- **Security:** Use `--cipher-algo AES256` and `--digest-algo SHA512` for maximum security.  
- **File Overwriting:** Use `--output` to prevent overwriting unintended files.  

ဒီ options တွေကို သင့်လိုအပ်ချက်အတိုင်း ရွေးပြီး စမ်းသုံးနိုင်ပါသည်။ ! 😊



---
---
---



# **High-Level Security**  GPG encryption ဖြစ်ပါတယ်။  

**Example Commands Combined**
   ```bash
   gpg --batch --yes --passphrase-file passwd.txt --symmetric --digest-algo SHA512 --cipher-algo AES256 --output secure_file.gpg file.zip
   ```
### **အဓိပ္ပါယ်နဲ့ သက်ဆိုင်တဲ့ Security အချက်များ**
1. **`--batch`**  
   Automation-friendly ဖြစ်အောင် interactive prompt မပါဘဲ run ဖို့။  
   - Scripting tools နဲ့လည်း အလွယ်တကူ သုံးလို့ရတယ်။

2. **`--yes`**  
   Existing files overwrite လုပ်ဖို့ automatic confirm ပေးတယ်။  
   - အသုံးပြုတဲ့အချိန်မှာ user interaction မလိုတော့ဘူး။

3. **`--passphrase-file passwd.txt`**  
   Password ကို CLI ထဲမှာ hardcode မလုပ်ဘဲ file ထဲကနေ ဖတ်တတ်တာဖြစ်တာမို့ လုံခြုံမှုပိုတိုးတယ်။

4. **`--symmetric`**  
   Password-based encryption လုပ်တာဖြစ်ပြီး **Public/Private Key** မလိုအပ်ဘဲ symmetric method နဲ့ data ကို secure လုပ်တယ်။

5. **`--digest-algo SHA512`**  
   Digest algorithm အနေနဲ့ **SHA512** ကို သုံးတာက hash security အဆင့်အမြင့်ဆုံးဖြစ်တာကြောင့် password verification process ကို အရမ်းခိုင်မာစေတယ်။

6. **`--cipher-algo AES256`**  
   Symmetric encryption algorithm အနေနဲ့ **AES256** ကို သုံးတာကြောင့် Military-grade security အတန်းဖြစ်ပြီး data ကို brute-force attack အတွက် အလွန်ခက်ခဲစေတယ်။

7. **`--output secure_file.gpg`**  
   Output file ကို manual သတ်မှတ်ထားတာဖြစ်ပြီး default overwrite လုပ်လို့ File corruption ရှောင်ကြဉ်နိုင်တယ်။

8. **Input File:** `file.zip`  
   File ကို zip format နဲ့ ဖိုင်ဆွဲပြီး encryption လုပ်တာဖြစ်လို့ အဆင်ပြေတယ်။ 

---

### **Security Features Summary**
- **Digest Algorithm:** SHA512 (အမြင့်ဆုံး hashing algorithm)  
- **Cipher Algorithm:** AES256 (အတန်းမရှိတဲ့ strong symmetric encryption)  
- **Automation:** CLI scripting-friendly  
- **Password Handling:** Secure passphrase file usage  

### **Security Level**  
✅ **High-Level Security**  
✅ **Script Automation-Compatible**  
✅ **လုံခြုံမှုအမြင့်ဆုံး Encryption Standards**  

ဒါကြောင့် ဒီ command က high-sensitive data အတွက်အသုံးပြုဖို့ အထူးသင့်တော်။ 💪