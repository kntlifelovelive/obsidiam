


### Script Breakdown

#### 1. **Banner ထုတ်ပြခြင်း**
```bash
clear
figlet "Encrypt & Decrypt" | boxes -d cat | lolcat
```

- **`clear`**: Terminal မှာရှိပြီးသား text တွေကို ဖျက်ပြီး terminal ကို သန့်စင်သွားစေတယ်။
- **`figlet`**: User အတွက် စာသား (ASCII Art) တစ်ခုကို ပေါ်ထွက်စေပါတယ်။ ဥပမာ `Encrypt & Decrypt` ဆိုတဲ့ စာသား။
- **`| boxes -d cat`**: `figlet` ကထွက်လာတဲ့ ASCII Art ကို box ဖွင့်ပြီး အလှဆင်ပေးတယ်။ `-d cat` က box style ကို "cat" လို့ သတ်မှတ်တာ။
- **`| lolcat`**: Final output ကို Rainbow color ရောင်စုံနဲ့ ပေါ်လာအောင် လုပ်ပေးတယ်။

---

#### 2. **အရွေးချယ်မှု မေးမြန်းခြင်း**
```bash
echo "Your choice (1 = Encryption, 2 = Decryption):" | lolcat
read choice
```

- **`echo`**: "Your choice" စာသားကို terminal မှာပြပြီး အသုံးပြုသူကို input ပေးဖို့ မေးမြန်းတယ်။
- **`| lolcat`**: Rainbow colors ထည့်ထားတာ။
- **`read choice`**: User input ကို `$choice` variable ထဲမှာ သိမ်းထားပြီး အောက်မှာအသုံးပြုမယ်။

---

#### 3. **Encryption လုပ်စဉ်**
```bash
if [ "$choice" -eq 1 ]; then
```

- **`if` statement**: `$choice` က 1 နဲ့ တူဆိုရင် Encryption လုပ်ဖို့ logic ကို သွားအောင် သတ်မှတ်တယ်။
- **`-eq`**: Numeric comparison (`1` နဲ့ သေချာတူလား စစ်တယ်)။

---

#### 4. **Encryption Input မေးခြင်း**
```bash
echo "Enter your encryption data (file to encrypt):" | lolcat
read data_path
```

- **`echo`**: "Enter your encryption data" ဆိုပြီး User input မေးတယ်။
- **`read data_path`**: User input ကို `$data_path` ဆိုတဲ့ variable ထဲမှာ သိမ်းထားတယ်။ အထဲမှာ encrypt လုပ်ဖို့ file path ထည့်ရမယ်။

---

```bash
echo "Enter your encryption protection password file (password.txt path):" | lolcat
read password_file
```

- **`read password_file`**: Password file ရဲ့ path ကို variable ထဲ သိမ်းတယ်။

---

```bash
echo "Enter the output file name (e.g., encrypted.gpg):" | lolcat
read output_file
```

- **`read output_file`**: Encrypt ထွက်လာမယ့် output file name ကို သိမ်းတယ်။

---

#### 5. **Encryption Command**
```bash
gpg --batch --yes --passphrase-file "$password_file" --symmetric \
    --digest-algo SHA512 --cipher-algo AES256 --output "$output_file" "$data_path"
```

- **`gpg`**: GNU Privacy Guard - Encryption/Decryption အတွက် CLI tool။
- **`--batch --yes`**: Automation အတွက် prompting မရှိအောင် စီစဉ်ထားတာ။
- **`--passphrase-file "$password_file"`**: Password ကို ထည့်သွင်းထားတဲ့ file ကို သုံးတယ်။
- **`--symmetric`**: Symmetric encryption method ကို အသုံးပြုတယ်။
- **`--digest-algo SHA512`**: Data integrity အတွက် SHA512 hashing algorithm သုံးတယ်။
- **`--cipher-algo AES256`**: Data encryption အတွက် AES256 algorithm သုံးတယ်။
- **`--output "$output_file"`**: Encrypt လုပ်ပြီးရင် ထွက်လာမယ့် file ကို `output_file` ဆိုပြီး သတ်မှတ်တယ်။
- **`"$data_path"`**: Encrypt လုပ်မယ့် original file path (user input)။

---

#### 6. **Encryption Success or Fail Message**
```bash
if [ $? -eq 0 ]; then
    echo "File encrypted successfully! Saved as $output_file" | lolcat
else
    echo "Encryption failed!" | lolcat
fi
```

- **`$?`**: Command runပြီးရတဲ့ exit status (0 = success, 1 or other = fail) ကို စစ်တယ်။
- **`-eq 0`**: Command က အောင်မြင်ပါက success message ပြတယ်။
- **`else`**: Encryption အောင်မမြင်ပါက fail message ပြတယ်။

---

#### 7. **Decryption Logic**
```bash
elif [ "$choice" -eq 2 ]; then
```

- `$choice` က 2 ဆိုရင် Decryption logic ကို run တယ်။

---

#### 8. **Decryption Input**
```bash
echo "Enter your decryption file (file to decrypt):" | lolcat
read encrypted_file
```

- **`read encrypted_file`**: Decrypt လုပ်မယ့် file path ကို သိမ်းတယ်။

```bash
echo "Enter your decryption protection password file (password.txt path):" | lolcat
read password_file
```

- Decrypt လုပ်ဖို့ password file ရဲ့ path ကို သိမ်းတယ်။

```bash
echo "Enter the output file name for decrypted data (e.g., decrypted.zip):" | lolcat
read output_file
```

- Decrypt ထွက်လာမယ့် file name ကို သိမ်းတယ်။

---

#### 9. **Decryption Command**
```bash
gpg --batch --yes --passphrase-file "$password_file" --decrypt \
    --output "$output_file" "$encrypted_file"
```

- **`--decrypt`**: Encrypted file ကို ဖြည့်စွက်တည်ဆောက်ထားတဲ့ password နဲ့ ဖွင့်တာ။
- `"$encrypted_file"`: Decrypt လုပ်မယ့် file path။
- `"$output_file"`: Decrypted output file path။

---

#### 10. **Invalid Input Message**
```bash
else
    echo "Invalid choice! Please select 1 for Encryption or 2 for Decryption." | lolcat
fi
```

- **`else`**: `$choice` က 1 သို့မဟုတ် 2 မဟုတ်ဘူးဆိုရင် Invalid Input Message ပြတယ်။

---

ဒီ script မှာ encryption/decryption လုပ်ဖို့ လွယ်ကူစွာ logic တွေချည်းပြီး အထက်ပိုင်းမှာ banner နဲ့ UI အလှဆင်ထားတာဖြစ်ပါတယ်။ `gpg` command က အဓိကအားဖြင့် အလုပ်လုပ်တယ်! 


---
---
## Encryption-&-Decryption-BashScript
---

```bash

#!/bin/bash

# Display Banner
clear
# figlet "Encrypt & Decrypt" | boxes -d cat | lolcat

figlet "En&Decrypt" | lolcat

# User Input
echo "Your choice (1 = Encryption, 2 = Decryption):" | lolcat
read choice

if [ "$choice" -eq 1 ]; then
    echo "Enter your encryption data (file to encrypt):" | lolcat
    read data_path
    echo "Enter your encryption protection password file (password.txt path):" | lolcat
    read password_file
    echo "Enter the output file name (e.g., encrypted.gpg):" | lolcat
    read output_file

    # Encryption Command
    gpg --batch --yes --passphrase-file "$password_file" --symmetric \
        --digest-algo SHA512 --cipher-algo AES256 --output "$output_file" "$data_path"

    if [ $? -eq 0 ]; then
        echo "File encrypted successfully! Saved as $output_file" | lolcat
    else
        clear
        echo "Encryption failed!" | lolcat
    fi

elif [ "$choice" -eq 2 ]; then
    echo "Enter your decryption file (file to decrypt):" | lolcat
    read encrypted_file
    echo "Enter your decryption protection password file (password.txt path):" | lolcat
    read password_file
    echo "Enter the output file name for decrypted data (e.g., decrypted.zip):" | lolcat
    read output_file

    # Decryption Command
    gpg --batch --yes --passphrase-file "$password_file" --decrypt \
        --output "$output_file" "$encrypted_file"

    if [ $? -eq 0 ]; then
        clear
        echo "File decrypted successfully! Saved as $output_file" | lolcat
    else
        echo "Decryption failed!" | lolcat
    fi

else
    echo "Invalid choice! Please select 1 for Encryption or 2 for Decryption." | lolcat
fi


```


---
---



# **Required Packages**
1. **GPG (GNU Privacy Guard)**  
   - Script မှာ encryption/decryption အတွက် `gpg` command ကို အသုံးပြုထားပြီး, အဓိကလိုအပ်ချက် ဖြစ်ပါတယ်။  
   ```bash
   sudo apt update && sudo apt install gnupg -y
   ```

2. **Lolcat**  
   - Text ကို အရောင်သွေးစုံစေပြီး ပိုမိုမြင်လွယ်အောင် ပြသရန် အသုံးပြုပါတယ်။  
```bash

   sudo apt install ruby
   
   sudo apt install gem
   
   sudo apt install wget

   wget https://github.com/busyloop/lolcat/archive/master.zip

   unzip master.zip

   cd lolcat-master/bin

   gem install lolcat




```

3. **Figlet**  
    
   ```bash
   sudo apt install figlet -y
   ```

---

### **Optional Packages**
1. **Fonts for Figlet** (If you want custom fonts)  
   - Custom fonts ရယူရန်အတွက်:

     ```bash
     sudo apt install figlet-toilet fonts-powerline -y
     ```

---

### **Installation Command (All-in-One)**  
 

```bash
sudo apt update && sudo apt install gnupg lolcat figlet -y
```

---

### **Verify Installation**
- GPG:  
  ```bash
  gpg --version
  ```
- Lolcat:  
  ```bash
  echo "Test Lolcat" | lolcat
  ```
- Figlet:  
  ```bash
  figlet "Test Figlet"
  ```

---
