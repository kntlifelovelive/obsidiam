
---

### TypeScript ဆိုတာဘာလဲ?

TypeScript ကတော့  
==> **JavaScript (JS)** ပေါ်အခြေခံပြီး  
==> **Static typing** ပေါင်းထည့်ထားတဲ့ **superset** တစ်ခုပဲဖြစ်ပါတယ်။

==> “TypeScript = JavaScript + Type System” ဖြစ်တယ်။

---

### 1. Variable Declaration

TypeScript မှာ variable တွေကို declare လုပ်တဲ့အခါ **type** specify လုပ်နိုင်တယ်။

```ts
let name: string = "Kyaw";
let age: number = 22;
let isStudent: boolean = true;
```

=> `:` နဲ့ type ကို assign လုပ်တာဖြစ်တယ်။

---

### 2. Type Inference

TypeScript ကတောင် **auto detect** လုပ်တတ်တယ်။

```ts
let country = "Myanmar"; // string type အဖြစ်သိတယ်
```

==> ဒီလိုဆိုရင် `country: string` လို့ မပြောပေမဲ့ TS ကပဲသိနေတယ်။

---

###  3. Array Types

Array ထဲက data type တစ်မျိုးတည်းဖြစ်ရမယ်။

```ts
let numbers: number[] = [1, 2, 3, 4];
let fruits: string[] = ["apple", "banana", "mango"];
```

---

###  4. Object Types

Object တစ်ခုရဲ့ data structure ကို type နဲ့ဖော်ပြနိုင်တယ်။

```ts
let person: { name: string; age: number } = {
  name: "Kyaw",
  age: 25
};
```

---

### 5. Functions

Function တွေမှာ input (parameter) type နဲ့ return type ကိုတိတိကျကျသတ်မှတ်နိုင်တယ်။

```ts
function greet(name: string): string {
  return "Hello, " + name;
}

console.log(greet("Bubu"));
```

---

### 6. Interface

Interface ကတော့ Object type ကို reusable ဖြစ်အောင်သုံးတာဖြစ်တယ်။

```ts
interface User {
  name: string;
  age: number;
  active: boolean;
}

const user1: User = {
  name: "Kyaw",
  age: 25,
  active: true
};
```

---

###  7. Union Types

Variable တစ်ခုမှာ type နှစ်မျိုးထက်ပိုနိုင်တယ်။

```ts
let id: string | number;
id = 101;
id = "AB123";
```

---

###  8. Type Alias

Type တွေကို အမည်တပ်ပြီး ပြန်သုံးလို့ရတယ်။

```ts
type ID = string | number;

let userId: ID = 123;
let adminId: ID = "admin-001";
```

---

###  9. Enum

Enum က constant values တွေကို အုပ်စုဖွဲ့တာဖြစ်တယ်။

```ts
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let move: Direction = Direction.Up;
```

---

###  10. Generics (အနည်းငယ် အဆင့်မြင့်)

Reusable function/class တွေကို type-safe ဖြစ်အောင်သုံးတယ်။

```ts
function identity<T>(value: T): T {
  return value;
}

let result1 = identity<string>("Hello");
let result2 = identity<number>(123);
```

---

###  Summary Table

|Concept|Example|Meaning|
|---|---|---|
|Variable|`let name: string = "Bubu"`|typed variable|
|Function|`(x: number): number`|typed parameters|
|Interface|`interface User { name: string }`|structure|
|Union|`string|number`|
|Generic|`<T>(value: T)`|reusable typing|
|Enum|`enum Color { Red, Green }`|constant set|

---

📘 **Note**

- `.ts` file ကို compile လုပ်မယ်ဆိုရင် → `tsc filename.ts`
- ပြီးရင် `filename.js` file ပြန်ထုတ်ပေးတယ်
- Type checking သုံးတာက run time error လျှော့စေတယ်။

---

