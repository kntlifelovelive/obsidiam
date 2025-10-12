
---

## **1. #!/bin/bash Vs #!/bin/env bash**

🔹 **`#!/bin/bash`**
- `/bin/bash` ဆိုတဲ့ fixed path ကို သုံးတယ် ။
- Bash shell ကို အတိအကျ ဒီနေရာမှာရှိမယ်လို့ ယူဆပြီး run တယ် ။
- Linux distribution အများစုမှာ `/bin/bash` ရှိတယ် (Debian, Ubuntu, Fedora, Arch စသည်) ။


```bash
#!/bin/bash
echo "This script uses /bin/bash"
```


🔹 **`#!/bin/env bash`**
- `env` command ကို သုံးပြီး Bash ကို **PATH environment variable** ထဲကနေရှာပြီး run တယ်။
- Bash ရဲ့ တိကျတဲ့နေရာကိုမသိပဲ run မယ်ဆိုရင် ဒီနည်းကပို flexible တယ်။ 
- တချို့ system တွေမှာ Bash က `/usr/bin/bash` သို့မဟုတ် `/usr/local/bin/bash` မှာရှိနိုင်တယ်။ 
-  ==> ဒီအခါ `#!/bin/env bash` သုံးမှ အဆင်ပြေတယ်။

```bash
#!/bin/env bash
echo "This script finds bash using env"
```

 **Note**
- `#!/bin/bash` → Faster, reliable on most systems (Linux default)
- `#!/bin/env bash` → Portable, system마다 bash location မတူတဲ့အခါ အသုံးပြု

## **2. ./test.sh vs ./test**

🔹 **`./test.sh`**
- `.sh` extension ပါတဲ့ script ကို အတိအကျ run တယ်
- Example → `test.sh` ဖိုင်ကို run

```bash
./test.sh
```


🔹 **`./test`**
- extension မပါတဲ့ script/file ကို run တာဖြစ်တယ်
- `.sh` extension မပါလည်း အဆင်ပြေတယ် (permission + shebang မှန်ရင်)

```bash
./test
```

- **မူလ script file name** ကွာသလောက် run နည်းက ကွာတာပဲ 
- `test.sh` ဆိုပြီး `.sh` နဲ့ သိမ်းထားရင် `./test.sh` သုံးရမယ်
- `test` ဆိုပြီး extension မထည့်ဘဲ သိမ်းထားရင် `./test` သုံးရမယ်
- တချို့ developer တွေက `.sh` တိုက်ရိုက်ထည့်တာနဲ့ script ဖိုင်ဆိုတာ သိသာအောင်ပြချင်လို့ `.sh` သုံးကြတယ်။
- System သက်ဆိုင်ရာအနည်းဆုံးအတွက်တော့ **extension မလိုဘဲ shebang + chmod +x** ရှိရင် ရမယ်။
### **Example**

```bash
#!/bin/bash
echo "Hello from test script"
```

- `test.sh` အနေနဲ့ save → `./test.sh` လိုရမယ်
- `test` အနေနဲ့ save → `./test` လိုရမယ်
- **Shebang အတွက်** → portable နည်းလိုရင် `#!/bin/env bash` သုံးပါ
- **Run command အတွက်** → extension မထားပဲ run မယ်ဆိုရင် `./test` လို run လိုက်လို့ရတယ်။

## **Shebang Recommend**

 **`#!/bin/env bash` သုံးတာ ပိုကောင်းတယ်**

- **Reason 1** → Portability (Linux တိုင်း Bash path မတူနိုင်, `/bin/bash` မရှိတဲ့ system မှာ fail မဖြစ်ဘူး)
- **Reason 2** → `env` က `$PATH` ထဲကနေ Bash ကိုလိုက်ရှာပေးလို့ script ကို ဘယ် Linux / Unix system ပေါ်မှာဖြစ်ဖြစ် run လိုက်လို့အဆင်ပြေတယ်။
- **Reason 3** → Future proof (တချို့ system တွေမှာ `/usr/bin/bash`, `/usr/local/bin/bash` ဆိုပြီး install လုပ်ထားနိုင်တယ်)

```bash
#!/bin/env bash
echo "This is portable Bash script"
```

## **Run command Recommend**

 **`./test` အတို run**
- Script file က `.sh` မထည့်လည်း အလုပ်လုပ်တယ် (chmod +x && shebang ပါလျှင်)
- Developer တွေ script ကို tool လို သုံးချင်ရင် `.sh` မထည့်ဘဲ အတို run တတ်ကြတယ်
- Example → `/usr/bin/ls` ကို `ls` လို သုံးသလိုပဲ
    -  `test` script တစ်ခု `PATH` ထဲထည့်ထားရင်
    - `test` လို run လိုက်ရုံနဲ့ ဘယ်နေရာကမဆို အလုပ်လုပ်နိုင်တယ်

- **Best practice** → `#!/bin/env bash` (portable + reliable)
- **Run style** → `./test` (clean + user-friendly)
## **Pro tip**

ဒီလို project tool လိုအသုံးချချင်ရင် အတို `test` သုံးတာ ကောင်းတယ်။ 

```bash
#!/bin/env bash
echo "Hello Kyaw 🤍"
```

`test` လို save →

```bash
chmod +x test
./test
```

 `PATH` ထဲထည့်လိုက်ရင် → `test` လို့ တိုတို run လိုက်ရုံနဲ့ အလုပ်လုပ်သွားမယ် 

---

