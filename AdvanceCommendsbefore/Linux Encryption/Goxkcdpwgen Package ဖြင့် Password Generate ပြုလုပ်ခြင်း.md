

## Ubuntu မှာ goxkcdpwgen ကို install လုပ်ပြီး အဲဒါနဲ့ `-c -s -n 1500 -d "-*#"`options တွေသုံးပြီး password generate ပြုလုပ်ခြင်း

---

## Step-by-Step Installation and Usage of `goxkcdpwgen`

## 1.Install `goxkcdpwgen pacakage`



  #### Terminal ကိုဖွင့်ပြီး `goxkcdpwgen` ကို install လုပ်ပါ:

```bash
    
sudo apt update

sudo apt search goxkcdpwgen

sudo apt install goxkcdpwgen

   
```

----

## 2.Generate Password

Command သည် password 1500 ခုကို -*# အထိ character တွေနဲ့ generate လုပ်ပြီး test.txt ဖိုင်ထဲသို့ ထည့်သွင်းတာဖြစ်ပါတယ်။


```bash

goxkcdpwgen -c -s -n 1500 -d "-*#" >> test.txt

goxkcdpwgen -c -s -n 120000 -d "^-*#@%" >> test.txt === better than of password strenght 


```  


 ###  *Explanation of the command options:*
```
   - -c: Use lowercase, uppercase, and numbers for the password.
   - -s: Include symbols in the generated password.
   - -n 1500: Generate 1500 passwords.
   - -d "-*#": Allow only the characters -, *, and # as symbols in the generated passwords.
   - >> test.txt: Redirect the output (the generated passwords) into a file called test.txt (it will append to the file if it already exists).

```

### 3.Check the Output

   Passwords တွေကို test.txt ဖိုင်ထဲမှာ ထည့်ပြီးပါပြီ။ ဖိုင်ကို command စစ်ဆေးနိုင်ပါတယ်။

```bash
      cat test.txt
```