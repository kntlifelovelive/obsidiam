

---

# *React မှာ `UI render` လုပ်တဲ့ နည်း ၃ မျိုး*


---

## နည်း ၁ — **Explicit Return (Curly Braces + return)**

```jsx
{data.map(item => {
  return <Item item={item} />
})}
```

**naming  → **Explicit return function**

- `=> { ... }` ဆိုပြီး **curly braces** ထဲမှာရေးထားလို့
- *Curly braces* ထဲကနေ `return` ဆိုပြီး အကြောင်းပြန်ပေးရမယ် ။ 
- usage :  — logic (if/else, calculation) ရှိပြီး JSX return လုပ်ချင်ရင်သုံးတယ်။


**Example**

```jsx
{data.map(item => {
  if (!item.visible) return null
  return <Item item={item} />
})}
```

---

## နည်း ၂ — **Implicit Return (Parentheses Only)**

```jsx
{data.map(item => <Item item={item} />)}
```

 **Naming call** → **Implicit return function**

- `=> (...)` ဆိုပြီး **parentheses** သုံးထားလို့
- `return` မလိုဘူး, JSX ကိုတိုက်ရိုက်ပြန်ပေးတယ်။
- အလွယ်ဆုံးနည်း, logic မရှိဘူးဆိုရင် သုံးရသင့်တဲ့နည်း။


 **Example**

```jsx
{data.map(item => <Item item={item} key={item.id} />)}
```

---

## နည်း ၃ — **Implicit Return with Multiple JSX Elements**

```jsx
{data.map(item => (
  <Item item={item} />,
  <Item item={item} />
))}
```

 **Naming call** → **Implicit return (Comma Operator)**

- JavaScript ရဲ့ **comma operator** သုံးထားလို့
- expression တွေကို အစဉ်လိုက် evaluate လုပ်ပြီး နောက်ဆုံးထဲကကို ပြန်ပေးမယ်
- ဒီနည်းက **weird** UI မှာ နောက်ဆုံး `<Item />` တစ်ခုသာ ပြသမယ်
- မသုံးသင့်ဘူး၊ အများစုက React community မှာ ဒီနည်းကို recommend မလုပ်ပါဘူး

 * **Example** (သုံးမယ့်နေရာနည်းနည်းကွဲပြား)

```jsx
{data.map(item => (
  <>
    <Item item={item} />
    <AnotherItem info={item.info} />
  </>
))}
```

 - ဒီလို **React Fragment** သုံးရင် element render properly ရမယ်

---

## အကြောင်းအရာချုပ်

| နည်း   | အမည်                          | သုံးသင့်တဲ့အချိန်                      |
| ------ | ----------------------------- | -------------------------------------- |
| နည်း ၁ | **Explicit Return**           | Logic ရှိရင်၊ condition သုံးရင်        |
| နည်း ၂ | **Implicit Return**           | Logic မလိုဘဲ JSX တိုက်ရိုက်ပြန်ချင်ရင် |
| နည်း ၃ | **Comma Operator (မထောက်ခံ)** | မသုံးသင့်ဘူး  `<></>` Fragment သုံး    |

---


-  နည်း ၂ (implicit return) သုံးတာအများဆုံး clean & readable ဖြစ်တယ်။  
-  အကယ်၍ `map()` ထဲမှာ if condition တွေလိုချင်ရင် နည်း ၁ သုံးပါ။  
- နည်း ၃ ကို JS စမ်းသပ်တဲ့နေရာမှာပဲ သုံး၊ production code မှာမသုံးသင့်ပါဘူး ။ 

---

