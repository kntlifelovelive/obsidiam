
---

##  React + Vite Project Create 

### 1. Vite Project Create

- Project Folder ထဲမှာ `npm init -y` အရင် ကြေငြာပေးမှ `Package json file` ရှိမှ `React Project create` လုပ်လို့ရသည်။ 

```bash

npm init -y 

# 1. project ဖိုင်ခေါ်မယ်
npm create vite@latest hello-react

npm create vite  <yourproject-name> 

```

==> `hello-react` ကို မင်းလိုချင်တဲ့ project name နဲ့ အစားထိုးနိုင်တယ်။ 

---

### 2. Option တွေရွေး

```bash
✔ Select a framework: › React
✔ Select a variant: › JavaScript (သို့) TypeScript
```

==> မင်း `TypeScript` နဲ့ စမ်းချင်ရင် **React + TypeScript** ရွေး၊  **React + JavaScript** ရွေး

---

### 3. Folder ထဲသွား

```bash
cd hello-react 

```

---

### 4. Dependency Install

```bash
npm install
```

---

### 5. Development Server Start 

```bash
npm run dev
```

*Default URL* 

```
http://localhost:5173
```

**vite.config.js** file မှာ auto browser ပွင့်အောင် json object server open ကို true ထည့် `npm run dev` ရင် auto browser open 

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
    open: true, 
  },
});

```

---

## Extra Notes

🔹 Yarn သုံးချင်ရင်

```bash
yarn create vite
```

🔹 Bun သုံးချင်ရင်

```bash
bun create vite
```

🔹 Project ကို Git init လုပ်ချင်ရင်

```bash
git init
git add .
git commit -m "First commit with Vite + React"
```

---

*Summary* 

- `npm create vite@latest my-app` → project create
- `cd my-app && npm install` → dependency install
- `npm run dev` → dev server run

---

## *Npm Command* 

```bash 
npm install bootstrap 

npm i bootstrap
npm i nodemon -g
npm i http-server -D
npm i jest -D

# http server run 
npm http-server 
npm run dev 

```

---


##  Modern React + Vite Project Structure

```
my-app/
│── public/                # Static assets (images, fonts, icons)
│
│── src/                   # Main source code
│   │── assets/            # App-wide assets (logo, css, images)
│   │── components/        # Reusable UI parts
│   │   │── atoms/         # Smallest components (Button, Input, Icon)
│   │   │── molecules/     # Combination of atoms (FormField, CardHeader)
│   │   │── organisms/     # Complex reusable sections (Navbar, Footer, Sidebar)
│   │   └── layouts/       # Page layouts (MainLayout, AuthLayout)
│   │
│   │── features/          # Feature-based modules
│   │   │── auth/          # Authentication module
│   │   │   │── components/  # LoginForm, SignupForm
│   │   │   │── hooks/       # useAuth.js
│   │   │   │── services/    # authAPI.js
│   │   │   └── pages/       # LoginPage.jsx, SignupPage.jsx
│   │   │
│   │   │── todo/          # Todo module
│   │   │   │── components/  # TodoList, TodoItem
│   │   │   │── hooks/       # useTodos.js
│   │   │   │── services/    # todoAPI.js
│   │   │   └── pages/       # TodoPage.jsx
│   │
│   │── hooks/             # Global reusable hooks (useFetch, useTheme)
│   │── context/           # React Context Providers (AuthContext, ThemeContext)
│   │── utils/             # Helper functions (dateFormat, validators)
│   │── services/          # API services (axios instance, API configs)
│   │── routes/            # App routes (React Router setup)
│   │── styles/            # Global styles (CSS, Tailwind, SCSS)
│   │── App.jsx            # Root component
│   │── main.jsx           # Entry point
│
│── package.json
│── vite.config.js
```

---

##  Example Usage

**1. Atom (Button.jsx)**

```jsx
export default function Button({ children, onClick }) {
  return <button onClick={onClick} className="btn">{children}</button>;
}
```

**2. Molecule (FormField.jsx)**

```jsx
import Button from "../atoms/Button";

export default function FormField() {
  return (
    <div>
      <input type="text" placeholder="Enter text..." />
      <Button>Submit</Button>
    </div>
  );
}
```

**3. Feature-based (todo/TodoPage.jsx)**

```jsx
import TodoList from "./components/TodoList";

export default function TodoPage() {
  return (
    <div>
      <h1>My Todo</h1>
      <TodoList />
    </div>
  );
}
```

---

##  Advantage of Modern Structure

- **Atomic design** → Reusable UI components
- **Feature-based** → တစ်ခုချင်း module လို separate logic
- **Scalable** → Project ကြီးလာလည်း maintain လွယ်
- **Clean imports** → index.js pattern သုံးပြီး import လွယ်

---

*Short Summary*

- `components/` → UI (atoms, molecules, organisms)
- `features/` → Functionality-based separation
- `hooks/`, `utils/`, `context/`, `services/` → reusable logic
- `routes/` → navigation system

---
## Modern style React + Vite 
*project folder structure  **command line generate**

##  Step by Step

### 1. Vite Project Create

```bash
# Main Project Folder follow run npm command 
npm init -y
npm create vite@latest <your-project-name> 
cd <your-project-path> 
npm install

```

---

### 2. Folder Structure Generate

```bash
# Main folders
mkdir -p src/{assets,components,features,hooks,context,utils,services,routes,styles}

# Atomic design folders
mkdir -p src/components/{atoms,molecules,organisms,layouts}

# Example feature modules
mkdir -p src/features/{auth,todo}

# Subfolders for each feature
mkdir -p src/features/auth/{components,hooks,services,pages}
mkdir -p src/features/todo/{components,hooks,services,pages}
```

---

### 3. Sample Files Generate

```bash
# Root files
touch src/App.jsx src/main.jsx

# Components
touch src/components/atoms/Button.jsx
touch src/components/molecules/FormField.jsx
touch src/components/organisms/Navbar.jsx
touch src/components/layouts/MainLayout.jsx

# Features (Auth)
touch src/features/auth/components/LoginForm.jsx
touch src/features/auth/hooks/useAuth.js
touch src/features/auth/services/authAPI.js
touch src/features/auth/pages/LoginPage.jsx

# Features (Todo)
touch src/features/todo/components/TodoList.jsx
touch src/features/todo/hooks/useTodos.js
touch src/features/todo/services/todoAPI.js
touch src/features/todo/pages/TodoPage.jsx

# Hooks, Context, Utils, Services
touch src/hooks/useFetch.js
touch src/context/AuthContext.jsx
touch src/utils/formatDate.js
touch src/services/api.js

# Routes
touch src/routes/AppRoutes.jsx

# Styles
touch src/styles/global.css
```

---

## Output Structure (after run)

```
src/
 ├─ assets/
 ├─ components/
 │   ├─ atoms/
 │   │   └─ Button.jsx
 │   ├─ molecules/
 │   │   └─ FormField.jsx
 │   ├─ organisms/
 │   │   └─ Navbar.jsx
 │   └─ layouts/
 │       └─ MainLayout.jsx
 │
 ├─ features/
 │   ├─ auth/
 │   │   ├─ components/LoginForm.jsx
 │   │   ├─ hooks/useAuth.js
 │   │   ├─ services/authAPI.js
 │   │   └─ pages/LoginPage.jsx
 │   └─ todo/
 │       ├─ components/TodoList.jsx
 │       ├─ hooks/useTodos.js
 │       ├─ services/todoAPI.js
 │       └─ pages/TodoPage.jsx
 │
 ├─ hooks/useFetch.js
 ├─ context/AuthContext.jsx
 ├─ utils/formatDate.js
 ├─ services/api.js
 ├─ routes/AppRoutes.jsx
 ├─ styles/global.css
 ├─ App.jsx
 └─ main.jsx
```

---
