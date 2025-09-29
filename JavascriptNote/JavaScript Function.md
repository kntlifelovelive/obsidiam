
# **1️⃣ Function ရေးနည်းများ**
JavaScript မှာ function တွေကို **(၁) Function Declaration, (၂) Function Expression, (၃) Arrow Function** တို့နဲ့ရေးနိုင်ပါတယ်။

---

## **📌 1.1 Function Declaration (မူလ Function ရေးနည်း)**
Function ကို `function` keyword နဲ့သတ်မှတ်ပြီး ရေးနိုင်ပါတယ်။

### **Syntax**
```js
function functionName(parameters) {
    // function body
    return result;
}
```

### **Example**
```js
function add(a, b) {
    return a + b;
}

console.log(add(5, 3)); // Output: 8
```
✅ **သိထားသင့်သည်**  
- `function add(a, b) {...}` ဆိုတာ function definition ဖြစ်တယ်။  
- `return` keyword သုံးလို့ function က output ကို return ပြန်ပေးတယ်။  
- `console.log(add(5,3))` ဆိုတာ function ကို call ခေါ်တာဖြစ်တယ်။  

---

## **📌 1.2 Function Expression (Function ကို Variable ထဲထည့်ပြီးသုံးနည်း)**
Function ကို variable ထဲမှာသိမ်းပြီး သုံးနိုင်ပါတယ်။

### **Syntax**
```js
const functionName = function(parameters) {
    // function body
    return result;
};
```

### **Example**
```js
const multiply = function(x, y) {
    return x * y;
};

console.log(multiply(4, 2)); // Output: 8
```
✅ **သိထားသင့်သည်**  
- Function ကို `const multiply = function(x, y) {...}` လို့ variable ထဲထည့်ပြီး သိမ်းထားတယ်။  
- ဒီလိုသုံးရင် function name မလိုပဲ **Anonymous Function** ဖြစ်သွားနိုင်တယ်။  

---

## **📌 1.3 Arrow Function (ES6 နဲ့ထွက်လာတဲ့ နည်းလမ်းအသစ်)**
Function ကို **=> (Arrow)** သုံးပြီး လွယ်လွယ်ရေးနိုင်ပါတယ်။

### **Syntax**
```js
const functionName = (parameters) => {
    // function body
    return result;
};
```

### **Example**
```js
const subtract = (a, b) => {
    return a - b;
};

console.log(subtract(10, 5)); // Output: 5
```
➡ **Single Line Arrow Function (Shorter Syntax)**  
```js
const subtract = (a, b) => a - b;
console.log(subtract(10, 5)); // Output: 5
```
✅ **သိထားသင့်သည်**  
- `=>` သုံးလိုက်တာနဲ့ function ကို လွယ်ကူပြီး syntax ကိုချုံ့ထားနိုင်တယ်။  
- **Single Statement** တစ်ခုတည်းပါက `{}` မလိုဘူး။  
- **Parameter တစ်ခုပဲ ရှိရင်** `()` မပါဘဲရေးလို့ရတယ်။  
```js
const square = x => x * x;
console.log(square(4)); // Output: 16
```

---

# **2️⃣ Function Parameter & Argument**
Function တွေဟာ **parameter (အချက်အလက်ရယူရန်) ကို ခံနိုင်ပြီး argument (တန်ဖိုး) ကိုပေးနိုင်ပါတယ်။**

### **Example**
```js
function greet(name) {
    return "Hello, " + name;
}

console.log(greet("Kyaw")); // Output: Hello, Kyaw
```
✅ **သိထားသင့်သည်**  
- `name` ဟာ parameter (function ရဲ့ input variable)  
- `"Kyaw"` ဟာ argument (function ကိုခေါ်တဲ့အခါ ပေးလိုက်တဲ့တန်ဖိုး)  

➡ **Multiple Parameters နဲ့ Function**
```js
function fullName(firstName, lastName) {
    return firstName + " " + lastName;
}

console.log(fullName("Aung", "Kyaw")); // Output: Aung Kyaw
```

---

# **3️⃣ Default Parameters (ES6 Feature)**
Function ကို ခေါ်တဲ့အခါ **argument မပေးဘူးဆိုရင် default value** တစ်ခုသတ်မှတ်နိုင်ပါတယ်။

### **Example**
```js
function greet(name = "Guest") {
    return "Hello, " + name;
}

console.log(greet());       // Output: Hello, Guest
console.log(greet("Kyaw")); // Output: Hello, Kyaw
```
✅ **သိထားသင့်သည်**  
- Function call မှာ argument မပေးရင် `name = "Guest"` ဟာ default value အနေနဲ့အသုံးပြုမယ်။  

---

# **4️⃣ Rest Parameters (`...`)**
Parameter အရေအတွက် မသိလို့ မတူညီတဲ့ argument တွေကို လက်ခံနိုင်တဲ့ function မျိုး။

### **Example**
```js
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```
✅ **သိထားသင့်သည်**  
- `...numbers` ဆိုတာ **rest parameter** ဖြစ်တယ်။  
- Function ကိုခေါ်တဲ့အခါ parameter များများပေးလို့ရတယ်။  
- `reduce()` function က **array ထဲက value တွေကို စုပြုလုပ်ပေးတာ** ဖြစ်တယ်။  

---

# **5️⃣ Function ကို Return မလုပ်ပဲ အသုံးပြုခြင်း (Void Function)**
บางครั้ง function တွေဟာ တန်ဖိုးမ return ပြန်ပဲ **message တွေပြခြင်း၊ console.log() နဲ့ output ပြခြင်း** စတာတွေ အလုပ်လုပ်နိုင်ပါတယ်။

### **Example**
```js
function showMessage(name) {
    console.log("Welcome, " + name + "!");
}

showMessage("Kyaw"); // Output: Welcome, Kyaw!
```
✅ **သိထားသင့်သည်**  
- `return` မသုံးဘဲ `console.log()` ကို သုံးလိုက်တာ။  
- ဒီလို function ကို Void Function (return မရှိတဲ့ function) လို့ခေါ်တယ်။  

---

# **6️⃣ Function ကို Argument အနေနဲ့ Passing ပြုလုပ်ခြင်း (Callback Function)**
Function တစ်ခုကို **argument အနေနဲ့ တခြား function ထဲသို့ ဖြတ်လွှဲနိုင်တယ်။**

### **Example**
```js
function doMath(a, b, operation) {
    return operation(a, b);
}

function multiply(x, y) {
    return x * y;
}

console.log(doMath(3, 4, multiply)); // Output: 12
```
✅ **သိထားသင့်သည်**  
- `multiply` function ကို `doMath` ထဲကို **argument အနေနဲ့** ပို့လိုက်တယ်။  
- `operation(a, b)` မှာ `multiply(3, 4)` ဆိုတဲ့ function ကို ခေါ်လိုက်တာ။  

---

# **Conclusion**
✔ **Function** ဆိုတာ reusable code block တစ်ခုဖြစ်ပြီး **function declaration, function expression, arrow function** နဲ့ရေးနိုင်တယ်။  
✔ **Parameter & Argument** တွေသုံးပြီး data တွေကို input ထည့်နိုင်တယ်။  
✔ **Default Parameters, Rest Parameters** တို့နဲ့ argument အလွယ်တကူ pass လုပ်နိုင်တယ်။  
✔ **Callback Function** တွေသုံးပြီး dynamic execution တွေလုပ်နိုင်တယ်။  

---