
# ${\color{green}Argon2 \space Option}$
CPU i7 7th Generation နှင့် 8GB RAM ရရှိထားသည့်စက်တွင် argon2 ကို အကောင်းဆုံး performance ဖြင့်အသုံးပြုရန် `-p`, `-t`, နှင့် `-m` options တွေကို ကျိုးကြောင်းဆီလျော်စွာ ချိန်ညှိနိုင်ပါတယ်။  

## ${\color{red} Option}$

1. `-p` (Parallelism)
   - `-p` သည် CPU threads ကို သတ်မှတ်သည်။
   - `-p 2` သို့ `-p 4` အသုံးပြုနိုင်ပါသည်။
   - CPU i7 7th Gen တွင် 4 physical cores နှင့် 8 logical threads ရှိသဖြင့် `-p 4` သည် hyper-threading ဖြင့် အကောင်းဆုံး performance ရရှိစေပါသည်။
   - Recommended: `-p 4` (4 threads)

2. `-t` (Time Cost)
   - `-t` သည် iterations count ကို သတ်မှတ်သည်။
   - Iteration count ပိုမြင့်လာသည်မည်မျှ security ပိုမိုတိုးတက်ပြီး processing time ကိုမြှင့်တင်စေပါသည်။
   - Recommended: `-t 3` သို့မဟုတ် `-t 4` (4 iterations)  
     - `-t 3` သည် ပုံမှန် Default ဖြစ်ပြီး 3 iterations အတွက် ပိုမိုလျင်မြန်သည်။
     - `-t 4` သည် တစ်ခါတည်း hash ကို ပိုမိုခက်ခဲစေပြီး security ပိုမိုမြင့်စေပါသည်။

3. `-m` (Memory Cost)
   - `-m` သည် memory usage ကို သတ်မှတ်သည်။
   - Memory cost ကို too high တိုးမြှင့်လိုက်ရင် system performance ကိုလည်း လျော့နည်းစေနိုင်သည်။
   - Recommended: `-m 16` (64 MiB)
     - `-m 16` သည် 64 MiB memory cost နှင့် system resources များကို ပိုမိုအသုံးပြုနိုင်ပါသည်။
     - `-m 18` (256 MiB) သည် ပိုမြင့်ပြီး system ရဲ့ resource ကို တစ်ပိုင်းအနည်းငယ် အကျိုးသက်ရောက်စေပါသည်။

### Best Configuration for i7 (7th Gen) & 8GB RAM

- `-p 4` (4 threads, hyper-threading)
- `-t 4` (4 iterations)
- `-m 16` (64 MiB memory cost)

#### Example Command
argon2 password123 -id -p 4 -t 4 -m 16

### Explanation  
- `-p 4`: Hyper-threading ကိုအသုံးပြုခြင်းဖြင့် 4 threads အသုံးပြုသည်။  
- `-t 4`: 4 iterations သည် security ကိုပိုမိုတိုးတက်စေပြီး performance နှင့် balance ပြုလုပ်ထားသည်။  
- `-m 16`: 64 MiB memory cost သည် 8GB RAM စက်အတွက် system ပေါ်တွင် ပိုမိုတန်ပြန်သော performance ရရှိစေပါသည်။

### Summary  
- CPU i7 7th Gen နှင့် 8GB RAM စက်အတွက် `-p 4`, `-t 4`, `-m 16` သည် အကောင်းဆုံး performance နှင့် security ကို တိုးတက်စေပါသည်။  
- `-p`, `-t`, `-m` value များကို system resource များနှင့် balance ပြုလုပ်နိုင်ပြီး `-t 3` သို့ `-m 18` တို့က တိုက်ရိုက်ပေါင်းထွေမှုရှိနိုင်သည်။ 

ဒါကြောင့် သင့်စက်အတွက် performance နှင့် security balance လုပ်ပြီး argon2 ကို ပိုမိုကောင်းမွန်စွာ အသုံးပြုနိုင်ပါတယ်။

---
---
## Argon2 နဲ့ sha512 တို့မှာ Argon2 ဟာ sha512 ထက် password hashing အတွက် ပိုမိုသင့်တော်ပီး password hashing  security ကိုပိုမိုကောင်းမွန်စွာ လုပ်ဆောင်ပေးနိုင်ပါတယ်။

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

####  **ထို့ကြောင့် argon2 ကို passwd.txt ကို hash ထုတ်ဖို့ သုံးသင့်ပါတယ်။🛡**