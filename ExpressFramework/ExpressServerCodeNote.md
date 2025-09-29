

---
## Express Server Code Explanation Note

### 1. Express  Import 

```js
const express = require("express");
```

- Node.js မှာ **Express framework** ကို သုံးဖို့ `require("express")` နဲ့ import လုပ်ထားရတယ်။

---

### 2. Express Application  Create

```js
const app = express();
```

- `app` က Express server ကို handle ပြုလုပ်မယ့် object (main application) ဖြစ်တယ်။

---

### 3. Define Route: `/items`

```js
app.get('/items', (req, res) => {
  res.json({ msg: "Hello Express: [items]" });
});
```

- `app.get()` ဆိုတာ **HTTP GET request** ကို handle ပြုလုပ်ဖို့ သုံးတယ်။

- Client က **GET /items** လို့ request လုပ်တဲ့အခါ response အနေနဲ့ JSON data `{ msg: "Hello Express: [items]" }` ကို ပို့ပေးမယ်။

---

### 4. Define Dynamic Route: `/items/:id`

```js
app.get('/items/:id', (req, res) => {
  const id = req.params.id; 
  res.json({ msg: `Hello Express : [items , ${id}]`});  
});
```

- `/items/:id` ဆိုတာ **Dynamic route** (parameterized route) ဖြစ်တယ်။

- `:id` ဆိုတဲ့ variable ကို Express က **req.params.id** နဲ့ ယူနိုင်တယ်။

- Request: `GET /items/100`

- Response: `{ msg: "Hello Express : [items , 100]" }`


---

### 5. Server  Run Code

```js
app.listen(8800, () => {
  console.log("Hello Express Running at port 8800 ...");
});
```

- Server ကို **port 8800** မှာ listen လုပ်စေတယ်။

- Start လုပ်သွားတဲ့အခါ console မှာ `"Hello Express Running at port 8800 ..."` လို့ print တယ်။

---

##  Run & Test

### Run Server

```bash
node index.js
Or 
npx nodemon --your javascript file < index.js > 


```

### Test with Browser or curl

- **[http://localhost:8800/items](http://localhost:8800/items)**

```json 
  { "msg": "Hello Express: [items]" }
  
```

- **[http://localhost:8800/items/5](http://localhost:8800/items/5)**

```js

{ "msg": "Hello Express : [items , 5]" }

```
---

