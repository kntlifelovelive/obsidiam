

## ***Argon2 နဲ့ sha512 တို့မှာ Argon2 ဟာ password hashing အတွက် ပိုမိုသင့်တော်ပါတယ်။ Argon2 ဟာ password hashing ကို security ပိုမိုကောင်းမွန်စွာ လုပ်ဆောင်ပေးနိုင်ပါတယ်။***

## 1. Argon2
- argon2 ဟာ password hashing အတွက် ပိုမိုတည်ငြိမ်တဲ့ နည်းလမ်းဖြစ်ပြီး adaptive ဖြစ်ပါတယ်၊ ဒါဆိုတော့ တစ်ချိန်လုံး ကျယ်ပြန့်တဲ့ compute power များကို လက်ခံနိုင်ပြီး အနာဂတ်တိုးတက်လာတဲ့ hardware များကို slow down ပြုလုပ်နိုင်ပါတယ်။
- argon2 ကို time cost, memory cost, နှင့် parallelism factor တို့ကို သတ်မှတ်နိုင်သလို၊ brute-force attack များကို ကြီးမားစွာ ကြံ့ခိုင်စေပါတယ်။
- ဤနည်းပညာသည် password cracking လုပ်သောသူများကို မျှော်လင့်လျှောက်လည်ရန် ပိုမိုခက်ခဲစေပါသည်။

## 2. sha512
- sha512 ဟာ cryptographic hashing algorithm တစ်ခုဖြစ်ပြီး password hashing အတွက် သုံးသင့်လောက်ပါသော်လည်း၊ argon2 ပိုင်းတွင်လိုအပ်သည့် adaptive လုပ်ဆောင်မှု မပါပါဘူး။
- sha512 ဟာ computation speed မြင့်ပြီး brute-force attack တွေမှာ argon2 ကဲ့သို့ စွမ်းဆောင်ချက် မြန်ဆန်နိုင်ပါတယ်။

# ကွာခြားချက်များ
- *argon2 ဟာ memory-intensive ဖြစ်တဲ့အတွက် brute-force နည်းလမ်းတွေကို တားမြစ်ဖို့ ပိုကောင်းတဲ့ နည်းလမ်းဖြစ်ပါတယ်။*
- *sha512 သည် speed ရှိပြီး computation အတွက် အလွယ်ကူမှုရှိသော်လည်း password hashing အတွက် လုံခြုံမှုတွင် argon2 ထက် ကျော်ကြားပြီး အကျိုးရှိသည်။*

## အနာဂတ်လုံခြုံမှု
- **Argon2 သည် password hashing နဲ့ related ဖြစ်တဲ့ အနေအထားတွင် more secure ဖြစ်ပြီး password-related attack များကို အကြီးအကျယ် ပိတ်ဆို့နိုင်တဲ့ နည်းလမ်းဖြစ်ပါတယ်။**

#### **ထို့ကြောင့် argon2 ကို passwd.txt ကို hash ထုတ်ဖို့ သုံးသင့်ပါတယ်။🛡**