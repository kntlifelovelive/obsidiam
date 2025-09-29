

---

## Express + SQLite Setup Note

### 1. Project Initialize

```bash
mkdir helloExpress
cd helloExpress
npm init -y
```

### 2. Install Required Packages

```bash
npm install OR i express cors nodemon
```

 - `express` → server framework  

### 3. Basic Project Structure

```
express-sqlite-app/
 ├─ node_modules/
 ├─ index.js
 ├─ package.json
 └─ database.sqlite   # (DB file will be created automatically)
```

### 4. index.js (Basic Example)

```js
const express = require("express");
const sqlite3 = require("sqlite3").verbose();

const app = express();
const db = new sqlite3.Database("./database.sqlite");

// Create table if not exists
db.run(`CREATE TABLE IF NOT EXISTS users(
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT
)`);

// Routes
app.get("/", (req, res) => {
  res.send("Hello Express + SQLite!");
});

app.get("/add/:name", (req, res) => {
  const name = req.params.name;
  db.run("INSERT INTO users (name) VALUES (?)", [name], function (err) {
    if (err) return res.send("Error: " + err.message);
    res.send(`User added with ID: ${this.lastID}`);
  });
});

app.get("/users", (req, res) => {
  db.all("SELECT * FROM users", [], (err, rows) => {
    if (err) return res.send("Error: " + err.message);
    res.json(rows);
  });
});

// Start server
app.listen(3000, () => console.log("Server running at http://localhost:3000"));
```

---

#### *Note*
- Express API local server ကို Run တဲ့အခါ autoupdate ဖို့ nodemon ဖြင့် Run ပါ။ 


```bash 
npx nodemon --your javascript file < index.js > 

```
