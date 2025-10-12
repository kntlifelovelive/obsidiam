
---

##  **`mkdir` Command – Make Directory**

🔹 **Usage:** `mkdir [options] directory_name`  
🔹 **Full form meaning:** _Make Directory_  
🔹 **Purpose:** Linux မှာ **ဖိုလ်ဒါအသစ် (directory)** ဖန်တီးဖို့ အသုံးပြုပါတယ်။

##  **Basic Syntax**

```bash
mkdir [OPTION] DIRECTORY_NAME
```

##  **Common Options**

|Option|Description|
|---|---|
|`-p`|Parent directories အလိုအလျောက် ဖန်တီးပေးတယ် (nested directories)|
|`-v`|Verbose mode — command လုပ်သမျှ directory တွေကို ပြပေးတယ်|
|`-m MODE`|Directory permission (like chmod) ကို သတ်မှတ်ပေးနိုင်တယ်|


##  **6 Practical Examples of `mkdir` Command**

### 1. Create a single directory

```bash
mkdir MyFolder
```

==> `MyFolder` ဆိုတဲ့ folder တစ်ခု လက်ရှိ directory ထဲ ဖန်တီးတယ်။

### 2. Create multiple directories at once

```bash
mkdir Folder1 Folder2 Folder3
```

==> တပြိုင်နက်မှာ directory ၃ ခု ဖန်တီးနိုင်တယ်။

### 3. Create nested directories (parent + child)

```bash
mkdir -p Projects/Python/Scripts
```

==> `Projects` → `Python` → `Scripts` directories ကို **တပြိုင်နက်ဖန်တီးတယ်**။


### 4. Create directory with verbose output

```bash
mkdir -v NewDir
```

==> “`mkdir: created directory 'NewDir'`” လို့ ပြပေးတယ်။


### 5. Create directory with specific permissions

```bash
mkdir -m 755 MySecureDir
```

==>  Directory ကို permission 755 (rwxr-xr-x) ဖြင့် ဖန်တီးတယ်။


### 6. Combine with `ls` to verify

```bash
mkdir TestDir && ls
```

==>  Directory ဖန်တီးပြီးနောက် လက်ရှိ folder ထဲမှာ စစ်ဆေးပြပါတယ်။


##  **Quick Summary Table**

|Command|Description|
|---|---|
|`mkdir MyFolder`|Create a single directory|
|`mkdir Folder1 Folder2`|Create multiple directories at once|
|`mkdir -p Parent/Child`|Create nested directories|
|`mkdir -v DirName`|Verbose output while creating directory|
|`mkdir -m 755 SecureDir`|Create directory with permissions|
|`mkdir Dir && ls`|Create and verify immediately|


##  **Brace Expansion with `mkdir`**

### 🔹 Syntax

```bash
mkdir {dir1,dir2,dir3}
```

==> ဒီကောဒ်က **dir1, dir2, dir3** တို့ကို တပြိုင်ထဲ  ဖန်တီးပေးပါတယ်။

### 🔹 Example 1 – Basic

```bash
mkdir {Test1,Test2,Test3}
```

==> လက်ရှိ folder ထဲမှာ  
`Test1`, `Test2`, `Test3` directories တပြိုင်နက် ဖန်တီးပါမယ်။


### 🔹 Example 2 – Nested directories

```bash
mkdir -p Project/{Python,JavaScript,HTML}/Src
```

==> **Brace Expansion + -p** ကိုပေါင်းပြီး  
`Project/Python/Src`, `Project/JavaScript/Src`, `Project/HTML/Src` directories အကုန်ကို တပြိုင်နက် ဖန်တီးနိုင်ပါတယ်။

### 🔹 Example 3 – Combine with sequence expansion

```bash
mkdir Folder{1..5}
```

==>  Folder1, Folder2, Folder3, Folder4, Folder5 directories အကုန်ဖန်တီးတယ်။


### Note Quick Tip

- Brace expansion ကို **`,`** နဲ့ directory names ခွဲတယ်။
- **`..`** နဲ့ sequence တည်ဆောက်နိုင်တယ်။
- **`-p`** ကို ထပ်ပေါင်းသုံးပြီး nested directories ဖန်တီးနိုင်တယ်။


 **Summary Table**

|Command|Result|
|---|---|
|`mkdir {A,B,C}`|Creates A, B, C directories|
|`mkdir Folder{1..3}`|Creates Folder1, Folder2, Folder3|
|`mkdir -p Project/{Python,JS}/Src`|Creates nested directories for Python and JS|

---
