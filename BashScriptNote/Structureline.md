
---
##### A = b+c`*`d ;(b=2,c=3,d=5)

*Bash arithmetic 2 way*

---

## 1 `expr` နည်း

```bash
#!/bin/bash
b=2
c=3
d=5

A=$(expr $b + $c \* $d)
echo "A = $A"
```



- `expr` ဆိုတာ **Expression evaluator** (expression တွေကို ချိန်တွက်ပေးတဲ့ command line tool) 
- Syntax:
  ```bash
  
   expr operand1 operator operand2
   ```

- Bash ရဲ့ built-in arithmetic မသုံးဘဲ External command ကို ခေါ်သုံးတာ ဖြစ်တယ်။
- `*` ကို special character ဖြစ်လို့ `\*` လို escape ပေးရတယ်။
- `expr` နည်းက Bash  feature မဟုတ်ပဲ Unix ကတည်းကလာတဲ့ **external command** ပေါ့။

---

## 2 Arithmetic Expansion `(( ))` နည်း

```bash
#!/bin/bash
b=2
c=3
d=5

(( A = b + c * d ))
echo "A = $A"
```


- `(( ... ))` ဆိုတာ Bash ရဲ့ **Arithmetic Evaluation / Expansion** လို့ခေါ်တယ်။
- Bash built-in feature ဖြစ်ပြီး `expr` လို external command မခေါ်ဘဲ Shell အတွင်းမှာတင် တိုက်ရိုက်တွက်ပေးတယ်။
- Escape မလို၊ syntax က Python လိုပဲ ။
- Variable assign ဖြစ်သူက `(( A = ... ))` အတွင်းမှာ တိုက်ရိုက်လုပ်နိုင်တယ်။
- **`expr`** → Expression evaluator (external command, ဗဟို Unix tool)
- **`(( ))`** → Arithmetic evaluation / arithmetic expansion (Bash built-in syntax)
---
- *Note* Efficiency များ၊ လွယ်ကူကာ bug နည်းတာကတော့ `(( ))`  Bash built-in Arithmetic Expansion နည်းပါ။ 


---


