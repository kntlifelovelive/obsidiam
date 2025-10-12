
---

#  Part 2 – Functions, Interfaces, Generics (Deep Level)


##  (1) Functions – Parameters & Return Types

TypeScript မှာ function တွေဟာ  
==>Input (parameter)  
==> Output (return value)  
နှစ်ခုစလုံးအတွက် type တွေသတ်မှတ်နိုင်တယ်။

###  Example 1 – Basic Function

```ts
function add(a: number, b: number): number {
  return a + b;
}

console.log(add(10, 20)); // Output: 30
```

==> `a: number` ဆိုတာ parameter type  
`(): number` ဆိုတာ return type ဖြစ်တယ်။

---

###  Example 2 – Optional Parameter

Parameter တစ်ခုပျက်လို့ရအောင် `?` သုံးတယ်။

```ts
function greet(name: string, age?: number): string {
  if (age) return `Hello ${name}, you are ${age} years old!`;
  else return `Hello ${name}!`;
}

console.log(greet("Kyaw")); // Hello Kyaw!
console.log(greet("Bubu", 22)); // Hello Bubu, you are 22 years old!
```

---

###  Example 3 – Default Parameter

Default value သတ်မှတ်ချင်ရင် `=` သုံးတယ်။

```ts
function power(base: number, exponent: number = 2): number {
  return base ** exponent;
}

console.log(power(5));   // 25 (default exponent = 2)
console.log(power(5, 3)); // 125
```

---

##  (2) Interface – Data Structure Design

Interface ဆိုတာ **object type structure** ကို  
သတ်မှတ်ပြီး ပြန်သုံးလို့ရအောင်လုပ်ပေးတယ်။

---

###  Example 1 – Basic Interface

```ts
interface Student {
  name: string;
  age: number;
  grade: string;
}

const stu1: Student = {
  name: "Kyaw",
  age: 20,
  grade: "A"
};

console.log(stu1);
```

---

###  Example 2 – Function Inside Interface

```ts
interface Person {
  name: string;
  sayHi(): string; // function inside interface
}

const user: Person = {
  name: "Bubu",
  sayHi() {
    return `Hi, I'm ${this.name}!`;
  }
};

console.log(user.sayHi());
```

---

###  Example 3 – Interface Extending Another Interface

```ts
interface Animal {
  name: string;
}

interface Dog extends Animal {
  breed: string;
}

const myDog: Dog = {
  name: "Lucky",
  breed: "Labrador"
};

console.log(myDog);
```

---

##  (3) Generics – Flexible Type Functions

Generics ဆိုတာ function, interface, class တို့ကို **type-safe**  
နဲ့ **reusable** ဖြစ်အောင်လုပ်ပေးတဲ့ နည်းပညာပါ။

---

###  Example 1 – Generic Function

```ts
function identity<T>(value: T): T {
  return value;
}

console.log(identity<number>(100));
console.log(identity<string>("Hello TypeScript"));
```

==> ဒီမှာ `<T>` ဆိုတာ “type placeholder” ဖြစ်တယ်။  
ဒါကြောင့် `T` ကို later မှာ number, string တို့အနေနဲ့ သုံးနိုင်တယ်။

---

###  Example 2 – Generic Array Function

```ts
function getFirst<T>(arr: T[]): T {
  return arr[0];
}

console.log(getFirst<number>([10, 20, 30])); // 10
console.log(getFirst<string>(["a", "b", "c"])); // "a"
```

---

###  Example 3 – Generic Interface

```ts
interface Box<T> {
  content: T;
}

const box1: Box<number> = { content: 123 };
const box2: Box<string> = { content: "Hello" };

console.log(box1, box2);
```

---

##  လေ့ကျင့်ဖို့ Assignments

1️=> Function တစ်ခုပေးပါ → `multiply(a,b)` ဆိုပြီး number နှစ်ခုယူပြီး ပြန်ပေးပါ။  
_Try adding default parameter (e.g. b=1)_
2️=> Interface `Car` တစ်ခုတည်ဆောက်ပါ → `brand`, `year`, `start()` ပါအောင်ရေးပါ။
3️=> Generic function `reverseArray<T>` တစ်ခုရေးပါ → array ကိုပြောင်းပြန်ပြန်ပေးပါ။

 Example expected result:

```ts
reverseArray<number>([1,2,3]); // [3,2,1]
reverseArray<string>(["a","b","c"]); // ["c","b","a"]
```

---

